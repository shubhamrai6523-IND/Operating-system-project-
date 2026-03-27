def fcfs(requests, head):
    print("\n--- FCFS ---")
    seek_time = 0

    for req in requests:
        print(f"Head moves from {head} → {req} | Seek = {abs(head - req)}")
        seek_time += abs(head - req)
        head = req

    print("Total Seek Time =", seek_time)


def sstf(requests, head):
    print("\n--- SSTF ---")
    seek_time = 0
    reqs = requests[:]

    while reqs:
        closest = min(reqs, key=lambda x: abs(x - head))
        print(f"Head moves from {head} → {closest} | Seek = {abs(head - closest)}")
        seek_time += abs(head - closest)
        head = closest
        reqs.remove(closest)

    print("Total Seek Time =", seek_time)


def scan(requests, head, disk_size=200):
    print("\n--- SCAN ---")
    seek_time = 0

    left = sorted([r for r in requests if r < head])
    right = sorted([r for r in requests if r >= head])

    # Move right
    for r in right:
        print(f"Head moves from {head} → {r} | Seek = {abs(head - r)}")
        seek_time += abs(head - r)
        head = r

    # Go to end
    print(f"Head moves from {head} → {disk_size} (end)")
    seek_time += abs(head - disk_size)
    head = disk_size

    # Move left
    for r in reversed(left):
        print(f"Head moves from {head} → {r} | Seek = {abs(head - r)}")
        seek_time += abs(head - r)
        head = r

    print("Total Seek Time =", seek_time)


def cscan(requests, head, disk_size=200):
    print("\n--- C-SCAN ---")
    seek_time = 0

    left = sorted([r for r in requests if r < head])
    right = sorted([r for r in requests if r >= head])

    # Move right
    for r in right:
        print(f"Head moves from {head} → {r} | Seek = {abs(head - r)}")
        seek_time += abs(head - r)
        head = r

    # Jump to beginning
    print(f"Head moves from {head} → {disk_size} (end)")
    seek_time += abs(head - disk_size)

    print(f"Jump from {disk_size} → 0")
    head = 0

    # Move right again
    for r in left:
        print(f"Head moves from {head} → {r} | Seek = {abs(head - r)}")
        seek_time += abs(head - r)
        head = r

    print("Total Seek Time =", seek_time)


# Example Input
requests = [98, 183, 37, 122, 14, 124, 65, 67]
head = 53

fcfs(requests, head)
sstf(requests, head)
scan(requests, head)
cscan(requests, head)
