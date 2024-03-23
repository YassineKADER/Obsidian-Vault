```Java
public class Node <T>{
	protected T data;
	protected Node<T> next = null;
	
	public Node(T data) {
		this.data = data;
	}
	
	public T getdata() {
		return this.data;
	}
	
	public Node getnext() {
		return this.next;
	}
}
```

```Java
public class LinkedList<T> {
	Node<T> head = null;
	private int listcount;

	public LinkedList() {
		listcount = 0;
	}

	public void show() {
		Node<T> showed_node = head;
		while (showed_node != null) {
			System.out.println(showed_node.getdata());
			showed_node = showed_node.next;
		}
	}

	private void decreassecount() {
		if (listcount > 0) {
			listcount--;
		}
	}

	public void add(T data) {
		Node end = new Node<T>(data);
		if (head == null) {
			head = end;
		}
		else {
			Node current = head;
			while (current.next != null) {
				current = current.next;
			}
			current.next = end;
		}
		listcount++;
	}

	public int size() {
		return listcount;
	}

	public void removeat(int index) {
		Node current = head;
		if (index > listcount || index < 0) {
			System.out.println("Out Of Range");
		} else if (index == 0) {
			head = head.next;
			decreassecount();
		} else {
			int jump = 0;
			while (jump < index - 1) {
				current = current.next;
				jump++;
				current.next = current.next.next;
				System.out.println("element removed !!");
				decreassecount();

			}

		}
	}

	public void removelast() {
		Node current = head;
		while (current.next.next != null) {
			current = current.next;
		}

		current.next = null;

		decreassecount();
	}

	public void removefirst() {
		if (head.next != null) {
			head = head.next;
		} else {
			head = null;
		}
		decreassecount();
	}

	public void remove(T data) {
		if (head.getdata() == data && head != null) {
			head = head.next;
		} else {
			Node current = head;
			while (current.next != null) {
				if (current.next.getdata() == data) {
					current.next = current.next.next;
					decreassecount();
					break;
				}
				current = current.next;
			}
		}
	}

	public void addfirst(T data) {
		Node<T> addedelement = new Node<T>(data);
		addedelement.next = head;
		head = addedelement;
		listcount++;

	}

	public void addAtIndex(T d, int index) {
		Node end = new Node(d);
		Node current = head;
		int jump;
		
		if (listcount < index || index < 0) {
			System.out.println("Index Out Of Range !!!");
		} else {
    		jump = 0;
    		while(jump<index-1){
    			current = current.next;
    			jump++;
    		}
    		end.next = current.next;
    		current.next = end;
    		listcount++;
		}
	}

}
```