---
title: KMP改进
date: 2017-10-21 18:34:16
tags: 算法
---
````c++
void getNext(string substr, int next[])
{
	int i = 0,j = -1;
	next[0] = -1;
	while (i<substr.length() - 1)
	{
		if (j == -1 || substr[i] == substr[j])
		{
			++i;
			++j;
			/*next[i] = j;*/
			if (substr[i] != substr[j])
			{
				next[i] = j;
			}
			else
			{
				next[i] = next[j];
			}
		}
		else
			j = next[j];
	}
}
int KMP(string str, string substr)
{
	int* next = new int[substr.length()];
	getNext(substr, next);
	int i = 0,j = 0;
	while (i<str.length() && j<substr.length())
	{
		if (j == -1 || str[i] == substr[j])
		{
			++i;
			++j;
		}
		else
		{
			j = next[j];
		}

	}
	if (j >= substr.length())
	{
		return i - substr.length();
	}
	return -1;
}
````