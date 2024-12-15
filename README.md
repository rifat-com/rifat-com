#include <stdio.h>
#include <stdlib.h>
struct Node {
	int diu;
	struct Node *left, *right;
};
struct Node* newNodeCreate(int value)
{
	struct Node* temp
		= (struct Node*)malloc(
			sizeof(struct Node));
	temp->diu = value;
	temp->left = temp->right = NULL;
	return temp;
}

struct Node* insertNode(struct Node* node, int value)
{
	if (node == NULL) {
		return newNodeCreate(value);
	}
	if (value < node->diu) {
		node->left = insertNode(node->left, value);
	}
	else if (value > node->diu) {
		node->right = insertNode(node->right, value);
	}
	return node;
}
void inOrder(struct Node* root)
{
	if (root != NULL) {
		inOrder(root->left);
		printf(" %d ", root->diu);
		inOrder(root->right);
	}
}


int main()
{
	struct Node* root = NULL;
	root = insertNode(root, 55);
	insertNode(root, 35);
	insertNode(root, 25);
	insertNode(root, 45);
	insertNode(root, 75);
	insertNode(root, 65);
	insertNode(root, 85);
	printf("Tree Elements: \n");
	inOrder(root);

	return 0;
}
