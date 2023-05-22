# This directory contains solution to the lesson-09
#include <iostream>
#include <vector>
#include <algorithm>

class IntegerSequence {
public:
    virtual std::vector<int> Numbers() = 0;
};

class VectorSequence : public IntegerSequence {
public:
    explicit VectorSequence(const std::vector<int>& numbers) : numbers(numbers) {}

    std::vector<int> Numbers() override {
        return numbers;
    }
private:
    std::vector<int> numbers;
};

class PositiveSequence : public IntegerSequence {
public:
    explicit PositiveSequence(std::unique_ptr<IntegerSequence> integersequence) : integersequence_(move(integersequence)) {}

    std::vector<int> Numbers() override {
        std::vector<int> numbers = integersequence_->Numbers();
        std::vector<int> positiveNumbers;

        for (int numbers : numbers) {
            if (numbers >= 0) {
                positiveNumbers.push_back(numbers);
            }
        }

        return positiveNumbers;
    }
private:
    std::unique_ptr<IntegerSequence> integersequence_;
};

class EvenSequence : public IntegerSequence {
public:
    explicit EvenSequence(std::unique_ptr<IntegerSequence> integersequence) : integersequence_(move(integersequence)) {}

    std::vector<int> Numbers() override {
        std::vector<int> numbers = integersequence_->Numbers();
        std::vector<int> evenNumbers;

        for (int num : numbers) {
            if (num % 2 == 0) {
                evenNumbers.push_back(num);
            }
        }

        return evenNumbers;
    }
private:
    std::unique_ptr<IntegerSequence> integersequence_;
};

class SortedSequence : public IntegerSequence {
public:
    explicit SortedSequence(std::unique_ptr<IntegerSequence> integersequence) : integersequence_(move(integersequence)) {}

    std::vector<int> Numbers() override {
        std::vector<int> numbers = integersequence_->Numbers();
        std::sort(numbers.begin(), numbers.end());
        return numbers;
    }
private:
    std::unique_ptr<IntegerSequence> integersequence_;
};

int main() {
    std::vector<int> init_vector = { 1,4,8,2,-8,0,13 };
    std::unique_ptr<IntegerSequence> integersequence = std::make_unique<PositiveSequence>(
            std::make_unique<EvenSequence>(
                std::make_unique<SortedSequence>(
                    std::make_unique<VectorSequence>(init_vector))));

    std::vector<int> num = integersequence->Numbers();

    for (int i : num) {
        std::cout << i << " ";
    }
    return 0;
}
