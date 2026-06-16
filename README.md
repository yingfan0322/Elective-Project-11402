# Elective-Project-11402
import random

def random_group_numbers(x, y, n):
    """
    Generates a list of numbers from x to y (inclusive),
    shuffles them, and divides them into n.

    Args:
        x (int): The starting number of the range.
        y (int): The ending number of the range.
        n (int): The desired number of groups.

    Returns:
        list: A list of lists, where each inner list is a random group of numbers.
    """

    

    if n <= 0:
        raise ValueError("Number of groups must be positive.")
    if x > y:
        raise ValueError("start_num cannot be greater than end_num.")

    all_numbers = list(range(x, y + 1))
    random.shuffle(all_numbers)

    total_numbers = len(all_numbers)
    if total_numbers == 0:
        return [[] for _ in range(n)] # Return empty groups if no numbers

    base_group_size = total_numbers // n
    remainder = total_numbers % n
    groups = []
    current_index = 0
    for i in range(n):
        group_size = base_group_size + (1 if i < remainder else 0)
        if group_size > 0:
            groups.append(all_numbers[current_index : current_index + group_size])
            current_index += group_size
        else:
            groups.append([]) # Append an empty group if no numbers can be assigned

    return groups

x = int(input("請輸入起始數值:"))
y = int(input("請輸入終止數值:"))
n = int(input("請輸入組別數量:"))
randomly_assigned_groups = random_group_numbers(x, y, n)

print(f"從編號 {x} 到 {y} 隨機分成 {n} 組:")
for i, group in enumerate(randomly_assigned_groups):
    print(f"第 {i+1} 組: {group}")
