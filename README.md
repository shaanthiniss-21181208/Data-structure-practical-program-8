class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None


class DoublyLinkedList:
    def __init__(self):
        self.head = None

    # Insert at end
    def insert(self, data):
        new_node = Node(data)

        if self.head is None:
            self.head = new_node
            return

        temp = self.head
        while temp.next:
            temp = temp.next

        temp.next = new_node
        new_node.prev = temp

    # Delete node
    def delete(self, key):
        temp = self.head

        while temp:
            if temp.data == key:
                if temp.prev:
                    temp.prev.next = temp.next
                if temp.next:
                    temp.next.prev = temp.prev
                if temp == self.head:
                    self.head = temp.next
                return
            temp = temp.next

        print("Value not found")

    # Display forward
    def display_forward(self):
        temp = self.head
        while temp:
            print(temp.data, end=" <-> ")
            temp = temp.next
        print("NULL")

    # Display backward
    def display_backward(self):
        temp = self.head
        while temp and temp.next:
            temp = temp.next

        while temp:
            print(temp.data, end=" <-> ")
            temp = temp.prev
        print("NULL")


# Driver Code
browser = DoublyLinkedList()

browser.insert("Page1")
browser.insert("Page2")
browser.insert("Page3")
browser.insert("Page4")

print("Forward Navigation:")
browser.display_forward()

print("Backward Navigation:")
browser.display_backward()

browser.delete("Page2")

print("After deleting Page2:")
browser.display_forward()# Data-structure-practical-program-8
