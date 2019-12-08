# Update-BST
My Second Repository on githb
Update every key in BST to contain the sum of all greater keys.

class Node {
	int data;
	Node left, right;

	Node(int data) {
		this.data = data;
	}
};

class Main {

	
	public static void inorder(Node root)
	{
		if (root == null) {
			return;
		}

		inorder(root.left);
		System.out.print(root.data + " ");
		inorder(root.right);
	}


	public static Node insert(Node root, int key)
	{
		
		if (root == null) {
			return new Node(key);
		}

		if (key < root.data) {
			root.left = insert(root.left, key);
		}
	
		else {
			root.right = insert(root.right, key);
		}

		return root;
	}

	public static int findSum(Node root)
	{
		if (root == null) {
			return 0;
		}

		return root.data + findSum(root.left) + findSum(root.right);
	}
	public static int update(Node root, int sum)
	{
		
		if (root == null) {
			return sum;
		}
		sum = update(root.left, sum);
	
		sum = sum - root.data;

		root.data += sum;
	
		sum = update(root.right, sum);

		return sum;
	}

	public static void main(String[] args)
	{
		Node root = null;
		

		int[] keys = { 5, 3, 2, 4, 6, 8, 10 };
		for (int key : keys) {
			root = insert(root, key);
		}

		int sum = findSum(root);
		update(root, sum);
		inorder(root);
	}
}
