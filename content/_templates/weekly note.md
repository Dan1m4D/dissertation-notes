---
weekStart: <% tp.date.now("YYYY-MM-DD", -((tp.date.now("e") + 6) % 7)) %>
weekEnd: <% tp.date.now("YYYY-MM-DD", 6 - ((tp.date.now("e") + 6) % 7)) %>
tags: #weekly 
---
# 🗓️ Weekly Note - <% tp.date.now("gggg-[W]WW") %>

## 📊 Weekly Goals

- **Main objectives:**
	- 
	- 
	- 
- **Deadlines:**
	- 
	- 
---

## 📊 Task Summary

> [!success] ✅ Tasks Done This Week
> ```dataviewjs
>const start = dv.date("<% tp.date.now("YYYY-MM-DD", -((tp.date.now("e") + 6) % 7)) %>");
>const end = dv.date("<% tp.date.now("YYYY-MM-DD", 6 - ((tp.date.now("e") + 6) % 7)) %>");
>
>function isDoneThisWeek(t) {
>    if (!t.completed) return false;
>    const completedDate = dv.date(t.completion);
>    return completedDate >= start && completedDate <= end;
>}
>
>const doneTasks = [
 >   ...dv.pages('"work/01 - daily notes"').file.tasks.where(isDoneThisWeek),
 >   ...dv.pages('"work/02 - weekly notes"').file.tasks.where(isDoneThisWeek),
 >   ...dv.pages('"work/03 - meetings"').file.tasks.where(isDoneThisWeek)
>];
>
>if (doneTasks.length === 0) dv.paragraph("No tasks done this week.");
>else dv.taskList(doneTasks, true);
> ```

> [!todo] 📋 Tasks This Week
> ```dataviewjs
>const { update } = app.plugins.plugins["metaedit"].api;
> 
> const tasks = [
>     ...dv.pages('"work/01 - daily notes"').file.tasks.where(t => !t.completed && !t.path.includes("_templates")),
>     ...dv.pages('"work/02 - weekly notes"').file.tasks.where(t => !t.completed && !t.path.includes("_templates")),
>     ...dv.pages('"work/03 - meetings"').file.tasks.where(t => !t.completed && !t.path.includes("_templates"))
> ];
> 
> if (tasks.length === 0) {
>     dv.paragraph("No pending tasks.");
> } else {
>     dv.taskList(tasks, false);
> }
>
> // Watch for task completion
> app.workspace.on("task-status-change", async (task, status) => {
> 	if (status === "done") {
> 		const today = window.moment().format("YYYY-MM-DD");
> 		await update("completion", today, task.path);
> 	}
> });
> ```

---

## 📓 Dissertation Weekly Summary

- Progress:
    
- Issues:
    
- Next week plan:
    
---

## 👥 Meetings This Week

```dataviewjs
const meetings = dv.pages('"work/03 - meetings"')
  .where(p => {
    if (!p.meeting_date) return false;
    const d = dv.date(p.meeting_date); // Dataview date
    return d && d >= dv.date("<% tp.date.now("YYYY-MM-DD", -((tp.date.now("e") + 6) % 7)) %>") && d < dv.date("<% tp.date.now("YYYY-MM-DD", 6 - ((tp.date.now("e") + 6) % 7)) %>");
  })
  .sort(p => dv.date(p.meeting_date), 'asc');

if (!meetings || meetings.length === 0) {
    dv.paragraph("No meetings this week.");
} else {
    const md = meetings.map(m => `- [[${m.file.name}]] (${dv.date(m.meeting_date).toFormat("ccc, dd MMM")})`).join("\n");
    dv.paragraph(md);

    const pre = document.createElement("pre");
    pre.textContent = md;
    pre.style.background = "#f7f7f7";
    pre.style.padding = "0.5em";
    pre.style.borderRadius = "4px";
    document.body.appendChild(pre);
}

```

---
## 📅 Dailies 

- [[<% tp.date.now("DD MMMM YYYY", -((tp.date.now("e") + 6) % 7)) %>]]  <!-- Monday -->
- [[<% tp.date.now("DD MMMM YYYY", -((tp.date.now("e") + 6) % 7) + 1) %>]]  <!-- Tuesday -->
- [[<% tp.date.now("DD MMMM YYYY", -((tp.date.now("e") + 6) % 7) + 2) %>]]  <!-- Wednesday -->
- [[<% tp.date.now("DD MMMM YYYY", -((tp.date.now("e") + 6) % 7) + 3) %>]]  <!-- Thursday -->
- [[<% tp.date.now("DD MMMM YYYY", -((tp.date.now("e") + 6) % 7) + 4) %>]]  <!-- Friday -->

---

## 🔗 Navigation

⬅️ [[work/02 - weekly notes/<% tp.date.now("gggg-[W]WW", -1) %>|Previous Week]] | 🟢 [[work/02 - weekly notes/<% tp.date.now("gggg-[W]WW") %>|This Week]] | ➡️ [[work/02 - weekly notes/<% tp.date.now("gggg-[W]WW", 1) %>|Next Week]]
