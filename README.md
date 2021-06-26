# Rust Book Chapter 17.3

## Trade-offs of the State Pattern

- Add a reject method that changes the post’s state from PendingReview back to Draft.
    - Added a new method `reject()` to **State** Just like the `approve()` method and called it and implemented it for **PendingReview** to return **Draft**.

- Require two calls to approve before the state can be changed to **Published**.
    - Added an enum called **ApprovalState** with possible values **NotApproved** and **FirstApproved**, and when `request_review()` is called, it returns the **PendingReview** struct with the enum value of **approval** set to **NotApproved**. When `approve()` is called for the first time, it returns **PendingReview** with **approval** as **FirstApproved**, and when it is called again, it retuns the **Published** struct.

- Allow users to add text content only when a post is in the Draft state. Hint: have the state object responsible for what might change about the content but not responsible for modifying the Post.
    - Not sure if its the right way but added a method to the **State** trait called, `get_name()`, which takes `&self` and returns `&str`, which is the name of the current state and then, in `add_text()` used an if statement to check if the name was **Draft** and only added the text if it was.

