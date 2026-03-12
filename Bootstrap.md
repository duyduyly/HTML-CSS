# Bootstrap Note


## Spacing
### Size
- Where property is one of:
  - `m` - for classes that set margin
  - `p` - for classes that set padding
- Where sides is one of:

- `t` - for classes that set margin-top or padding-top
- `b` - for classes that set margin-bottom or padding-bottom
- `s` - (start) for classes that set margin-left or padding-left in LTR, margin-right or padding-right in RTL
- `e` - (end) for classes that set margin-right or padding-right in LTR, margin-left or padding-left in RTL
- `x` - for classes that set both *-left and *-right
- `y` - for classes that set both *-top and *-bottom
- blank - for classes that set a margin or padding on all 4 sides of the element

| Class    | CSS value | Equivalent |
|----------|-----------|------------|
| `*-0`    | `0`       | 0          |
| `*-1`    | `0.25rem` | 4px        |
| `*-2`    | `0.5rem`  | 8px        |
| `*-3`    | `1rem`    | 16px       |
| `*-4`    | `1.5rem`  | 24px       |
| `*-5`    | `3rem`    | 48px       |
| `*-auto` | `auto`    | auto       |


## Text
### Font-weight
| Bootstrap class | CSS equivalent         | Meaning            |
|-----------------|------------------------|--------------------|
| `fw-light`      | `font-weight: 300`     | Light text         |
| `fw-normal`     | `font-weight: 400`     | Normal text        |
| `fw-medium`     | `font-weight: 500`     | Medium             |
| `fw-semibold`   | `font-weight: 600`     | Semi bold          |
| `fw-bold`       | `font-weight: 700`     | Bold               |
| `fw-bolder`     | `font-weight: bolder`  | Relative to parent |
| `fw-lighter`    | `font-weight: lighter` | Relative to parent |

### Line-height
| Class     | CSS value           | Approx. Percent | Meaning            |
|-----------|---------------------|-----------------|--------------------|
| `lh-1`    | `line-height: 1`    | 100%            | Very tight text    |
| `lh-sm`   | `line-height: 1.25` | 125%            | Small line spacing |
| `lh-base` | `line-height: 1.5`  | 150%            | Default spacing    |
| `lh-lg`   | `line-height: 2`    | 200%            | Large spacing      |
