---
tags: frontend, tailwindcss, engineering/frontend, variants, css
author: Tran Khac Vy
github_id: trankhacvy
date: 2023-07-13
---
In our tech hub in Dwarves Foundation, we prefer using tailwindcss for styling our components. When we start a new project, we focus on creating common components that are used throughout the app and apply tailwind css to style them. Let's take the button component as an example to demonstrate how we handle different styles from our design system.

```javascript
function getAppearanceButtonStyles({
  variant = 'primary',
  disabled = false,
}: GetAppearanceButtonStylesTypes) {
  const classNames = ['rounded-md shadow-sm font-medium border']
  const focusRing = 'focus:ring-2 focus:ring-offset-2 focus:outline-none'

  if (variant === 'default') {
    if (!disabled) {
      classNames.push(
        'border-gray-300 text-gray-700 bg-white hover:bg-gray-50 focus:ring-pink-500',
      )
      classNames.push(focusRing)
    } else if (disabled) {
      classNames.push('bg-gray-100 text-gray-400')
    }
  } else if (variant === 'primary') {
    if (!disabled) {
      classNames.push(
        'border-transparent text-white bg-pink-600 hover:bg-pink-700 focus:ring-pink-500',
      )
      classNames.push(focusRing)
    } else if (disabled) {
      classNames.push('bg-gray-100 text-gray-400')
    }
  } else if (variant === 'secondary') {
    if (!disabled) {
      classNames.push(
        'border-transparent text-white bg-gray-500 hover:bg-gray-600 focus:ring-gray-400',
      )
      classNames.push(focusRing)
    } else if (disabled) {
      classNames.push('bg-gray-100 text-gray-400')
    }
  }

  return classNames
}

const Button = (
  {
    variant = 'default',
    children,
    className,
    ...props
  }: PropsWithAs<ButtonProps>,
  ref: React.Ref<HTMLButtonElement>,
) => {

  return (
    <button
      ref={ref}
      {...props}
      className={cx(
        className,
        getAppearanceButtonStyles({ variant, disabled: props.disabled }),
      )}
    >
      {children}
    </button>
  )
}
```
The simplify version of our Button component.

Initially, we use if-else statements, which work well when the project is small. However, as the number of button styles increases (like solid, outline, ghost, transparent) and we have various colors (such as primary, secondary, success, error) and sizes (like xs, sm, md, lg), managing these if-else code blocks becomes complex and challenging. To address this issue, we decided to use library [Tailwind Variants](https://www.tailwind-variants.org/).


Tailwind Variants provides a user-friendly interface for defining variants that selectively apply sets of classes. It allows you to easily express default variants and even compound variants, where classes can be applied based on a combination of different variants. As an added benefit, incorporating the TypeScript type for variants into your component using the variant props type helper is straightforward and hassle-free.

Let's rewrite my Button component by using Tailwind variants

```javascript
import { tv } from 'tailwind-variants'

const focusRing = 'focus:ring-2 focus:ring-offset-2 focus:outline-none'

const buttonStyles = tv({
  base: 'relative font-medium',
  variants: {
    variant: {
      primary: '',
      secondary: '',
      default: '',
    },
    disabled: {
      true: '',
    },
  },
  compoundVariants: [
    {
      variant: 'primary',
      disabled: false,
      className: [
        'border-transparent text-white bg-pink-600 hover:bg-pink-700 focus:ring-pink-500',
        focusRing,
      ],
    },
    {
      variant: 'primary',
      disabled: true,
      className: 'bg-gray-100 text-gray-400',
    },
    {
      variant: 'secondary',
      disabled: false,
      className: [
        'border-transparent text-white bg-gray-500 hover:bg-gray-600 focus:ring-gray-400',
        focusRing,
      ],
    },
    {
      variant: 'secondary',
      disabled: true,
      className: 'bg-gray-100 text-gray-400',
    },
    {
      variant: 'default',
      disabled: false,
      className: [
        'border-gray-300 text-gray-700 bg-white hover:bg-gray-50 focus:ring-pink-500',
        focusRing,
      ],
    },
    {
      variant: 'default',
      disabled: true,
      className: 'bg-gray-100 text-gray-400',
    },
    {
      variant: ['primary', 'secondary', 'default'],
      className: 'rounded-md shadow-sm border',
    },
  ],
  defaultVariants: {
    disabled: false,
    variant: 'default',
  },
})

const Button = (
  {
    variant = 'default',
    children,
    className,
    ...props
  }: PropsWithAs<ButtonProps>,
  ref: React.Ref<HTMLButtonElement>,
) => {

  return (
    <button
      ref={ref}
      {...props}
      className={buttonStyles({ variant, disabled: props.disabled })}
    >
      {children}
    </button>
  )
}

```

By using Tailwind variants, your components become easier to understand and expand. This helps reduce the effort required to maintain them. Applying Tailwind variants to your entire app ensures a consistent way of integrating Tailwindcss into your components, making it simpler for your team to work together.

In addition, tailwind variants offer incredible features that make it effortless to create components that adapt to the design system:

- **Responsive variants**: You can apply variants to different screen sizes, making your components responsive.
- **Slots**: This feature allows you to break down a component into multiple parts, offering greater flexibility in customization.
- **Overrides**: You have the option to provide a `class`/`className` prop for overriding classes on any component, giving you more control over styling.
- **Components composition**: You can easily compose components using the extend parameter. It automatically combines the `classes`, `slots`, `variants`, `defaultVariants`, and `compoundVariants` of the extended component, simplifying component creation.
- **TypeScript support**: Tailwind variants seamlessly integrate with TypeScript, providing built-in support for type checking and enhanced development experience.
- **Automatic conflict resolution**: Under the hood, tailwind variants utilize `tailwind-merge`, which efficiently merges your classes to prevent conflicts. This ensures a smooth and hassle-free styling process without worrying about class conflicts in TailwindCSS.

## Conclusion
In conclusion, the adoption of Tailwind Variants has greatly enhanced our component styling approach at Dwarves Foundation. With its user-friendly interface, we are able to effortlessly define and apply variants, enabling seamless customization and alignment with our design system. The support for responsive variants, slots for component breakdown, overrides for precise control, and seamless TypeScript integration make Tailwind Variants an invaluable tool for creating adaptable and maintainable components in our development workflow.

## References
- https://www.tailwind-variants.org/
- https://cva.style
- https://stitches.dev/
