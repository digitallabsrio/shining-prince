# Available numbers are 1, 2, and 4
def count_ways(n):
    # Initializing our solution array
    dp = [0] * (n + 1)

    # Each array index holds the number of ways to
    # reach a number equal to the index
    dp[0] = 1

    # Variables to store sub-target numbers
    n1 = n3 = n4 = 0

    # Iteratively calculate the number of ways to reach a
    # target number and store it in the solutions' array
    for sn in range(1, n+1):
        # Return 0 if index is less than 0, otherwise
        # set to array value
        n1 = 0 if sn - 1 < 0 else dp[sn - 1]
        n3 = 0 if sn - 3 < 0 else dp[sn - 3]
        n4 = 0 if sn - 4 < 0 else dp[sn - 4]

        # Using our recurrence relation to calculate new answers
        dp[sn] = n1 + n3 + n4
    return dp[n]

def main():
    target_numbers = [3, 5, 10, 25, 0]

    # You can uncomment the line below and check how this bottom-up solution executes without a time-out
    # target_numbers.append(50)

    for i in range(len(target_numbers)):
        num_ways = count_ways(target_numbers[i])
        print(i+1, ".", "\tNumber of ways to reach the target number ", target_numbers[i], ": ", num_ways, sep="")
        print("-" * 100)
        print()

if __name__ == '__main__':
    main()