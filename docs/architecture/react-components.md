React Component Standards

Client vs Server
- Default to Server Components.
- Use Client Components for state, effects, and browser APIs.
- Keep Client Components small and leaf-level.

Organization
- One component per file unless tightly coupled.
- Co-locate component styles and tests.
- Prefer feature folders over type folders.

Props
- Keep props minimal and explicit.
- Avoid passing callbacks through many layers.
- Use `children` for layout-only composition.

State
- Lift state to the lowest shared parent.
- Avoid duplicating derived state.

Style
- Prefer CSS modules or scoped styles.
- Avoid inline styles except for dynamic values.

Example
```tsx
type CardProps = {
	title: string;
	children: React.ReactNode;
};

export function Card({ title, children }: CardProps) {
	return (
		<section className="card">
			<h2>{title}</h2>
			<div className="card-body">{children}</div>
		</section>
	);
}
```