TypeScript Notes 

1️⃣ What is TypeScript

Superset of JavaScript → JS + types
Helps catch bugs before runtime
Strongly typed → can’t mix types carelessly
Transpiled to JS → browser runs JS, not TS

2️⃣ Basic Types
string, number, boolean
array: string[] or Array<number>
object: { key: type }
any → disables type checking
unknown → safer alternative to any

3️⃣ Type Aliases & Interfaces
type User = { id: number; name: string; isAdmin?: boolean }
interface Product { id: number; title: string; price: number }

Optional property → ?
Interfaces usually for objects, type aliases also for unions/generics

4️⃣ Functions
function add(a: number, b: number): number { return a + b }
const greet = (name: string): string => `Hello ${name}`

(param: type) => returnType
Enforces type safety for inputs and outputs

5️⃣ Union & Literal Types
let id: string | number
let status: "success" | "error"

Union (|) → variable can have multiple types
Literal → restrict to exact values

6️⃣ Generics (Basics)
function wrap<T>(value: T): { value: T } { return { value } }

Reusable with any type
Common in reusable components/hooks

7️⃣ React + TypeScript
Props
interface ButtonProps { label: string; onClick: () => void }
const Button: React.FC<ButtonProps> = ({ label, onClick }) => <button onClick={onClick}>{label}</button>

State
const [count, setCount] = useState<number>(0)

Event Handlers
const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => console.log(e.target.value)

8️⃣ Next.js + TypeScript
Page Props
interface HomeProps { users: { id: number; name: string }[] }
const Home: React.FC<HomeProps> = ({ users }) => <div>{users.map(u => <p key={u.id}>{u.name}</p>)}</div>

API Routes
import type { NextApiRequest, NextApiResponse } from 'next'
type User = { id: number; name: string }

export default function handler(req: NextApiRequest, res: NextApiResponse<User[]>) {
  res.status(200).json([{ id: 1, name: 'Alice' }])
}