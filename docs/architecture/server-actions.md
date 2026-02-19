Server Actions Standards

Purpose
- Use Server Actions for mutations and secure data access.

Design
- Keep actions focused on one operation.
- Validate inputs at the action boundary.
- Return minimal data needed by the caller.

Errors
- Throw domain errors with clear messages.
- Map unexpected errors to a safe response.

Caching
- Revalidate tags or paths after mutations.
- Avoid caching user-specific responses unless scoped.

Example
```ts
"use server";

import { revalidateTag } from "next/cache";

type CreateNoteInput = {
	title: string;
	body: string;
};

export async function createNote(input: CreateNoteInput) {
	if (!input.title.trim()) {
		throw new Error("Title is required");
	}

	await db.note.create({ data: input });
	revalidateTag("notes");
}
```