The default help key for `tmux` on an Ubuntu server (or any system) is **Ctrl+b ?**

Here's a breakdown:

* **Ctrl+b:** This is the default **prefix key** for `tmux`. You press and hold `Ctrl` and then press `b` (or whatever key you've configured as your prefix).
* **?:** After pressing the prefix key, you press the question mark key (`?`).

So, to access the `tmux` help, you would press:

**`Ctrl` + `b` then `?`**

This will display the `tmux` help screen in your current pane, showing you a list of available keybindings.

**Key points:**

* **Prefix Key:** Understanding the prefix key is essential to using `tmux`. It's what tells `tmux` that you're about to give it a command, not just type in the current pane.
* **Customization:** While `Ctrl+b` is the default prefix key, you can change it in your `tmux.conf` file if desired. This is a common practice for users who find `Ctrl+b` awkward.
* **Help Screen:** The help screen provides a comprehensive overview of `tmux` keybindings, including those for windows, panes, sessions, and more.

Okay, here's a tmux cheatsheet, covering the most common and useful commands. Remember, `Ctrl+b` is assumed as the default prefix key. If you've changed your prefix, replace `Ctrl+b` with your custom prefix.

**Basic Navigation & Session Management**

* **`Ctrl+b ?`:**  Show help (lists all keybindings)
* **`Ctrl+b d`:** Detach current session
* **`Ctrl+b s`:**  List sessions (and allows switching)
* **`Ctrl+b :new-session -s <session-name>`:** Create a new named session
* **`Ctrl+b :attach-session -t <session-name>`:** Attach to an existing session
* **`Ctrl+b :kill-session -t <session-name>`:** Kill a specific session
* **`Ctrl+b $`:** Rename current session
* **`tmux ls` (outside of tmux):** List all tmux sessions
* **`tmux a` (outside of tmux):** Attach to the most recent session
* **`tmux a -t <session-name>` (outside of tmux):** Attach to a specific session

**Window Management**

* **`Ctrl+b c`:** Create a new window
* **`Ctrl+b ,`:** Rename current window
* **`Ctrl+b n`:** Move to the next window
* **`Ctrl+b p`:** Move to the previous window
* **`Ctrl+b <window number>`:** Go to window by number (starting from 0)
* **`Ctrl+b w`:**  List windows (and allows switching)
* **`Ctrl+b &`:** Kill current window

**Pane Management**

* **`Ctrl+b "`:** Split pane horizontally (top/bottom)
* **`Ctrl+b %`:** Split pane vertically (left/right)
* **`Ctrl+b <arrow keys>`:** Move between panes (up, down, left, right)
* **`Ctrl+b z`:** Toggle zoom pane (maximize/restore)
* **`Ctrl+b x`:** Kill current pane
* **`Ctrl+b ;`:** Move to last active pane
* **`Ctrl+b o`:** Cycle through panes

**Copy Mode (Scrolling & Copying Text)**

* **`Ctrl+b [`:** Enter copy mode (allows scrolling and selecting text)
* **`Space`:** Start selection
* **`Enter`:** Copy selection to clipboard
* **`q`:** Exit copy mode
* **`PgUp` / `PgDn`:** Scroll up and down
* **`v`:**  Enter visual selection mode (same as pressing `Space`)
* **`Ctrl+b ]`:** Paste the clipboard content

**Other Useful Commands**

* **`Ctrl+b t`:** Display the time
* **`Ctrl+b Ctrl+o`:** Rotate panes (move the current pane to the next pane position)
* **`Ctrl+b !`:** Break a pane into a new window.
* **`Ctrl+b :`:** Opens the tmux command prompt (allows you to run `tmux` commands directly)
   * Example: `:split-window -h` (splits horizontally)
   * Example: `:resize-pane -Z` (toggles pane zoom)

**Important Notes**

* **Customization:** This is just a starting point. You can customize nearly every aspect of `tmux`, including keybindings, status bar appearance, and more.  This is usually done by modifying the `.tmux.conf` file in your home directory.
* **Practice:** The best way to learn `tmux` is to use it regularly. Start with the basic commands and gradually explore more advanced features as you become comfortable.
* **Context Matters:** Some commands might behave slightly differently depending on the context (e.g., copy mode, certain plugins).

**Example Usage**

1.  **Start a new named session:** `tmux new-session -s my_session`
2.  **Create a new window:**  `Ctrl+b c`
3.  **Split the current pane horizontally:** `Ctrl+b "`
4.  **Move to the new bottom pane:** `Ctrl+b <arrow down>`
5.  **Detach from the session:** `Ctrl+b d`
6.  **Reattach to the session:** `tmux attach -t my_session`

This cheatsheet should give you a good foundation for working with tmux. Remember to consult the help ( `Ctrl+b ?`) for a complete list of available commands and customization options! Good luck!

Okay, here's a table defining the key jargon words used within the context of `tmux`:

| Term        | Definition                                                                                                                                                                                          | Relationship                                                                                       | Analogy                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Session** | A persistent, independent container for one or more windows. A session can be detached (running in the background) and later re-attached, retaining its state. Think of it as a top-level "project".| Contains one or more windows; can be shared between clients.                                       | Like a project folder containing multiple documents (windows).                                            |
| **Client**  | An interactive connection to a `tmux` server. This is the terminal instance where you are actively interacting with `tmux`. You can have multiple clients attached to the same session.               | Connects to a session; you can have multiple clients attached to the same session, viewing the same output.| Like opening a project folder (session) in multiple file explorer windows (clients).                      |
| **Window**  | A single, full-screen display within a `tmux` session. Each window has its own set of panes and can be switched between. Can contain multiple panes (like tabs in a browser).                               | Contained within a session; contains one or more panes.                                           | Like a single file document in your project, that can be viewed/edited in multiple panels (panes)    |
| **Pane**    | A rectangular sub-region within a window. Panes allow you to display multiple programs or outputs simultaneously in a single window. (like a split view in an editor).                                 | Contained within a window; the basic building blocks of display.                                    | Like a split view in a code editor, allowing you to view multiple files or regions simultaneously |

**Key Takeaways & Relationships Visualized:**

*   **Hierarchical Structure:**  `tmux` is fundamentally organized in a hierarchy:  `Server` (the underlying tmux process) -> `Session` -> `Window` -> `Pane`
*   **Persistence:** Sessions persist even when clients are detached (disconnected). You can close the terminal window and the session continues to run in the background.
*   **Sharing:** Multiple clients can connect to the same session simultaneously, allowing for collaboration.
*  **Windows vs. Panes:** Windows are for switching between different *contexts*, while panes allow you to split and view multiple things *within* the same context.

**Analogy Explanation:**

Let's extend the "project folder" analogy:

*   **`tmux Server`**: The core application that manages the whole process.
*   **`Session`**: Your project folder containing all the code, documents, and data.
*   **`Client`**:  Your File Explorer or Editor Window opened, allowing you to interact with the project. You can open multiple instances (clients) to access the project.
*   **`Window`**: A specific document or file within the project folder, like the code file (`main.py` or a word document).
*   **`Pane`**: The areas in your code editor where you can split your file to see different parts or run commands.

Understanding these definitions will make it easier to use `tmux` effectively. Let me know if you'd like any more clarification!
