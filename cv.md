# Didar Auyesbay
### Junior Frontend Developer

---

### Contact information:

**Phone:** +7 705 715 65 74<br>
**E-mail:** didarmaratov04@gmail.com<br>
**Telegram:** @d3drrr<br>
[LinkedIn](https://www.linkedin.com/in/didar-auyesbay-370b0a281/) <br>

---

### Briefly About Myself:

I am fourth year student at Suleyman Demirel University. As a future frontend developer, I bring a creative mindset.<br>
With a strong commitment to continuous learning and staying up-to-date with the latest industry trends, I am eager to contribute my<br>
skills and grow as a professional frontend developer.

---

### Skills and Proficiency:

- HTML5, CSS3
- JavaScript
- Git, GitHub
- VS Code, IntelliJ IDEA
- Linux
- SQL
---

### Code example:

**Range Sum Query - Mutable from Leetcode:**
*Given an integer array nums, handle multiple queries of the following types:*

*Update the value of an element in nums.*
*Calculate the sum of the elements of nums between indices left and right inclusive where left <= right.*

```c++
class SegmentTree {
    vector<int> seg; // Segment Tree to be stored in a vector.
public:
    SegmentTree() {}
    SegmentTree(vector<int>& nums) {
        int n = nums.size();
        seg.resize(4 * n, 0);  // Maximum size of a segment tree for an array of size n is 4n
        buildTree(nums, 0, 0, n - 1); // Build the segment tree
    }
    void buildTree(vector<int>& nums, int pos, int left, int right) {
        if (left == right) {
            seg[pos] = nums[left];
            return;
        }
        int mid = left + (right - left) / 2;
        buildTree(nums, 2 * pos + 1, left, mid);
        buildTree(nums, 2 * pos + 2, mid + 1, right);
        seg[pos] = seg[2 * pos + 1] + seg[2 * pos + 2];
    }
    void updateTree(int pos, int left, int right, int idx, int val) {
        // no overlap
        if (idx < left || idx > right) return;
        
        // total overlap
        if (left == right) {
            if (left == idx) seg[pos] = val;
            return;
        }
        // partial overlap
        int mid = left + (right - left) / 2;
        updateTree(2 * pos + 1, left, mid, idx, val);
        updateTree(2 * pos + 2, mid + 1, right, idx, val);
        seg[pos] = seg[2 * pos + 1] + seg[2 * pos + 2];
    }
    
    int queryTree(int qleft, int qright, int left, int right, int pos) {
        if (qleft <= left && qright >= right) { // total overlap
            return seg[pos];
        }
        if (qleft > right || qright < left)  {  // no overlap
            return 0;
        }
        // partial overlap
        int mid = left + (right - left) / 2;
        return queryTree(qleft, qright, left, mid, 2 * pos + 1) + queryTree(qleft, qright, mid + 1, right, 2 * pos + 2);
    }
};

class NumArray {
    SegmentTree st;
    int n;  // Length of the num vector. 
public:
    NumArray(vector<int>& nums) {
        this->st = SegmentTree(nums);
        this->n = nums.size();
    }
    
    void update(int index, int val) {
        st.updateTree(0, 0, n - 1, index, val);
    }
    
    int sumRange(int left, int right) {
        return st.queryTree(left, right, 0, n - 1, 0);
    }
};
```
---

### Courses:

- HTML, CSS and Javascript for web developers [w3schools](https://www.w3schools.com/](https://www.coursera.org/learn/html-css-javascript-for-web-developers)) (completed)<br>
- Advanced Javascript and Typescript self-study (in progress)

---

### Languages:

- English \- Upper-intermediate IELTS 6,5 in 2021 | W&T in Alaska in 2024
- Kazakh \- Native
- Russian \- Fluent
