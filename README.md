# linkedList

#How to build a linked_list

#Node class
class Node:
    def __init__(self, data):
        self.data = data 
        self.next_node = None
#LinkedList class
class linkedList:

    def __init__(self):
        self.head = None
    #checking if the list is empty or not
    def is_empty(self):
        return self.head is None
    #adding value at the end of the list
    def append(self, data):
        new_node = Node(data)
        current = self.head
        if self.head is None:
            self.head = new_node
            return
        current_node = self.head
        while current_node.next_node:
            current_node = current_node.next_node
        current_node.next_node = new_node
    #adding data at the begining of the list
    def prepend(self, data):
        new_node = Node(data)
        new_node.next_node = self.head
        self.head = new_node
    #adding a data at a specific position
    def insert(self, data, index):
    #If we add data at position zero
        if index == 0:
            new = Node(data)
            new.next_node = self.head
            self.head = new
      #if we add data at position other than zero
        if index > 0:
            new = Node(data)
            position = index
            current = self.head
            while position > 1:
                current = current.next_node
                position -= 1
            prev_node = current
            nxt_node = current.next_node
            prev_node.next_node = new
            new.next_node = nxt_node

    #removing data from the linkedlist:
    def remove(self, key):
        current = self.head
        prv_node = None
        found = False
        while current and not found:
            if current.data == key and current is self.head:
                found = True
                self.head = current.next_node
            elif current.data == key:
                found = True
                prv_node.next_node = current.next_node
            else:
                prv_node = current
                current = current.next_node
        return current

        
    #String representation of linkedList
    def __str__(self):
        current = self.head
        nodes = []
        while current is not None:
            if current == self.head:
                r = f"[Head: {current.data}]"
                nodes.append(r)
            elif current.next_node is None:
                l = f"[Tail: {current.data}]"
                nodes.append(l)
            else:
                nodes.append(str(current.data))
            current = current.next_node
        return '-> '.join(nodes)
        


l = linkedList()
l.append(3)
l.append(32)
l.append(82)
l.append(822)
l.append(63)
l.prepend(1)
l.remove(1)
l.insert(8,0)
print(l)
