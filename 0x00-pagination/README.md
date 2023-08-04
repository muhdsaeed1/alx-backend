Pagination offers the ability to spread all of your results across multiple pages. For example, consider a blog with 10,000 posts. If my home page lists all of my blog posts, it'll show entirely too many to be seen by one viewer. So we split them into pages, showing 5 or 10 per page
Suppose we have a list of strings called book, if we page an index (0-indexed) into the book, and page_size, we have to find the list of words on that page. If the page is out of index then simply return an empty list.

So, if the input is like book = ["hello", "world", "programming", "language", "python", "c++", "java"] page = 1 page_size = 3, then the output will be ['language', 'python', 'c++']

To solve this, we will follow these steps −

l:= page*page_size

return elements of book from index l to l+page_size - 1

class Solution:
   def solve(self, book, page, page_size):
      l=page*page_size
      return book[l:l+page_size]
ob = Solution()
book = ["hello", "world", "programming", "language", "python", "c++",
"java"]
page = 1
page_size = 3
print(ob.solve(book, page, page_size))
