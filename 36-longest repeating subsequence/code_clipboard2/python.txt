def find_LRS(str):
    size = len(str)
    # Create a table to hold intermediate values
    lookup_table = [[0 for x in range(size + 1)] for y in range((size + 1))]

    # Starting from second row, filling the lookup table bottom-up wise
    for i in range(1, size + 1):
        for k in range(1, size + 1):
            # Characters are same but indexes are different
            if str[i - 1] == str[k - 1] and i != k:
                lookup_table[i][k] = lookup_table[i - 1][k - 1] + 1
            # Check if the characters at both indexes don't match
            else:
                lookup_table[i][k] = max(lookup_table[i - 1][k], lookup_table[i][k - 1])

    # Returning the longest repeating subsequence length
    return lookup_table[size][size]


# Driver code
def main():
    inputs = ["abcd", "abddccd", "abbaba", "aaaaba", "abcdaeda"]

    # Let's uncomment this and check the effect of dynamic programming with tabulation
    # inputs.append("abcdefghijklmnopqrstuv")

    for i in range(len(inputs)):
        print(str(i + 1) + ". String: "+str(inputs[i]))
        print("Longest repeating subsequence is", find_LRS(inputs[i]))
        print("-" * 100, "\n", sep="")


if __name__ == "__main__":
    main()