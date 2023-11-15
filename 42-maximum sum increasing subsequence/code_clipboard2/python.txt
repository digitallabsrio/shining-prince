def MSIS_length(nums):
    size = len(nums)
    # we created a table here
    dp = [[0]*(size+1) for i in range(size+1)]

    for curr in range(size-1, -1, -1):
        for prev in range(curr-1, -2, -1):
            length = dp[curr+1][prev+1]
            # if 'prev' is negative or previous value is less than the next value
            # we will take it
            if prev < 0 or nums[prev] < nums[curr]:
                length = max(length, nums[curr]+dp[curr+1][curr+1])
            dp[curr][prev+1] = length
    return dp[0][0]


# driver code
def main():
  lists = [[4, 1, 2, 6, 10, 1, 12], [-4, 10, 3, 7, 15], [4, 2, 3, 6, 10, 1, 12],
  [3, 2, 6, 4, 5, 1], [3, 2], [1, 2, 3, 4, 5, 6, 7],
  [1, 101, 2, 3, 100, 4, 5], [1, 5, 2, 3, 9, 5]]

  # Let's uncomment this to see the benefit of using dynamic programming with tabulation

  # lists.append([20, 46, 6, 82, 88, 34, 85, 86, 58, 29, 71, 74, 6, 71, 14, 60, 97, 19, 76, 63,
  #  39, 100, 16, 69, 99, 95, 55, 41, 23, 57, 90, 65, 39, 93, 4, 25, 73, 96, 81, 92, 38, 74, 2,
  #   43, 38, 47, 48, 34, 44, 19, 48, 4, 41, 70, 86, 16, 92, 3, 9, 83, 72, 39, 72, 61, 73, 16, 53,
  #    17, 94, 77, 17, 70, 56, 11, 40, 81, 22, 5, 21, 34, 0, 88, 72, 6, 69, 67, 0, 97, 45, 97, 0, 32,
  #     85, 70, 30, 95, 89, 3, 9, 77, 67, 0, 97, 45, 97, 0, 32, 85, 70, 30, 95, 89, 3, 9, 77, 70, 30,
  #      95, 89, 3, 9, 77, 67, 0, 97, 45, 97, 0, 32, 85])

  for i, input_list in enumerate(lists):
    print(i+1, ". Input array: ", input_list, sep="")
    print("Maximum sum of increasing subsequence is:", MSIS_length(input_list))
    print("-"*100)

if __name__ == '__main__':
  main()