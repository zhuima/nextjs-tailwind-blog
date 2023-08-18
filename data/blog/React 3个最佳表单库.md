---

title: React 开发者公认的三个最佳表单库
date: 2023/08/16 14:23:38
lastmod: 2023/08/16  14:23:42
tags: [Three Best React Form Libraries]
draft: false
summary: 了解基本的 React 表单库对开发人员至关重要，包括 React Hook Form、Formik 和 React Final Form。
images: https://img.techrk1688.eu.org/file/2f48fa7ea3ffc18460051.png
authors: ['default']
layout: PostLayout
---

随着 React 项目的表单变得越来越复杂，我们如何简化工作？在 React 中创建和处理表单可能具有挑战性且耗时。幸运的是，第三方库可以提供帮助。有许多特殊的表单库可用，可以简化流程并使 React 表单开发更加高效和愉快。

然后，主要问题变成了哪种形式的库是最好的。在这篇博文中，我们将讨论每个 React 开发人员都应该知道的三个顶级 React 表单库。

## 1. Formik

![](https://img.techrk1688.eu.org/file/cf9d0f07c69a071b93e85.png)

Formik 是一个广泛使用且非常流行的 React 应用程序表单库。它通过为开发人员提供一组工具和实用程序来帮助无缝处理表单状态、验证和提交，从而简化了表单管理。

### Formik's 的主要特点

- 声明性方法：开发人员可以使用 Formik 使用声明性语法创建表单，该语法最大限度地减少了对样板代码的需求并简化了表单结构，使其更加简洁。
- 表单状态管理：此工具有助于跟踪对表单元素所做的更改，并简化与表单的不同交互的处理。
- 验证：开发人员可以使用 Formik 提供的内置验证功能轻松定义表单字段的验证规则和错误消息。
- 表单提交：Formik 通过在提交期间处理异步任务（如 API 请求）来更轻松地提交表单。
- 与第三方库集成：Formik毫不费力地整合了知名库（例如用于基于模式的验证的Yup）和各种UI库（例如Material-UI）。

如果您正在寻找一种可靠的方法来在 React 应用程序中创建复杂且不断变化的表单，那么 Formik 值得考虑。其强大的社区支持和开发团队一直在努力改进它。

### Formik 用法

以下是如何使用 Formik 的基本概述：

- 安装：首先，您可以使用 npm 或 来 yarn 安装 Formik 及其对等依赖项 Yup（用于表单验证）：

```bash
npm install formik yup
# or
yarn add formik yup
```

- 导入和设置：从 Formik 和 Yup 导入所需的组件，然后使用该 Formik 组件设置表单：

```js
import React from 'react';
import { Formik, Form, Field, ErrorMessage } from 'formik';
import * as Yup from 'yup';

const initialValues = {
  name: '',
  email: '',
};

const validationSchema = Yup.object({
  name: Yup.string().required('Name is required'),
  email: Yup.string().email('Invalid email address').required('Email is required'),
});

const onSubmit = (values) => {
  console.log(values);
};

const MyForm = () => (
  <Formik
    initialValues={initialValues}
    validationSchema={validationSchema}
    onSubmit={onSubmit}
  >
    <Form>
      <div>
        <label htmlFor="name">Name</label>
        <Field type="text" id="name" name="name" />
        <ErrorMessage name="name" component="div" />
      </div>

      <div>
        <label htmlFor="email">Email</label>
        <Field type="email" id="email" name="email" />
        <ErrorMessage name="email" component="div" />
      </div>

      <button type="submit">Submit</button>
    </Form>
  </Formik>
);

export default MyForm;
```

- 字段和错误消息：组件 Field 用于输入信息，而 ErrorMessage 组件显示与字段中输入的数据相关的任何验证错误。
- 表单提交：Formik 负责表单状态、验证和提交表单时的状态。如果验证成功，将触发 Formik 组件中定义的 onSubmit 函数，传递表单值。
- 访问 Formik 状态：要在表单组件中访问 Formik 的状态和帮助程序，可以使用 useFormik 钩子或 withFormik 高阶组件。

Formik 提供了各种功能，包括处理表单重置、异步提交、动态表单字段等。上面的示例涵盖了基本方面，但您可以浏览 Formik 文档以发现高级用法和自定义选项。

## 2. React Hook Form

![](https://img.techrk1688.eu.org/file/4c652412d0eccc1be4c0a.png)

React Hook Form 是一个非常有效的表单库，它利用 React 的钩子来管理表单状态和行为。它优先考虑性能，旨在最大限度地减少重新渲染的次数，确保最佳的用户体验。

### React Hook Form 式主要特点

1. 最少的重新渲染：React Hook Form 经过优化，通过高级技术（例如更新受控和不受控制的组件）来减少不必要的重新渲染。
2. 自定义挂钩：鼓励开发人员使用自定义挂钩来管理表单状态。这种方法允许在不同应用程序部件中模块化和重用表单逻辑。
3. 验证：React Hook Form 是一种用于验证表单的通用且适应性强的工具。它提供内置和自定义验证方法，允许灵活处理不同的验证方案。
4. 异步验证：其功能之一是能够执行异步验证，这简化了根据远程 API 验证数据或执行复杂验证检查的过程。
5. 性能：React Hook Form 是高性能应用的理想选择，因为它最大限度地减少了频率。

### React Hook Form 用法

以下是在项目中使用 React Hook Form 的方法：

- 安装：首先，使用 npm 或 安装 yarn 库：

```bash
npm install react-hook-form
# or
yarn add react-hook-form

```

- 主要用途：首先，从库中导入必要的函数，然后创建表单组件。

```js
import { useForm, Controller } from 'react-hook-form';

function MyForm() {
  const { control, handleSubmit, formState } = useForm();

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <label>Name</label>
      <Controller
        name="name"
        control={control}
        defaultValue=""
        render={({ field }) => <input {...field} /> }
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

- 字段验证：React Hook Form 具有内置的验证支持，该支持利用基于模式的验证库，例如 yup 可以使用内联验证函数。

```js
import { useForm, Controller } from 'react-hook-form';
import * as yup from 'yup';

const schema = yup.object().shape({
  name: yup.string().required('Name is required'),
});

function MyForm() {
  const { control, handleSubmit, formState } = useForm({
    resolver: yupResolver(schema),
  });

  // ...

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <label>Name</label>
      <Controller
        name="name"
        control={control}
        defaultValue=""
        render={({ field, fieldState }) => (
          <div>
            <input {...field} />
            {fieldState.error && <p>{fieldState.error.message}</p>}
          </div>
        )}
      />
      {/* ... */}
    </form>
  );
}

```

- 高级用法：通过参考 React Hook Form 文档中提供的官方文档，探索 React Hook 表单的高级功能，例如动态字段、自定义输入和数组字段
- 访问表单状态：要访问表单状态和错误，请使用 useForm 挂钩提供 formState 的对象。

```js
const { handleSubmit, formState: { errors, isSubmitting } } = useForm();
```

- 性能优化：React Hook Form 旨在通过最大限度地减少重新渲染和不必要的更新来提高性能。它是通过不受控制的组件和表单状态的内部处理来实现的。因此，对受控组件重新渲染的需求较少。

必须参考官方文档和示例，以确保您拥有最新的信息，并在项目中实现 React Hook Form 时使用最佳实践。

## 3、React Final Form

React Final Form 是一个广泛使用的表单库，可以有效地管理 React 应用程序中的表单。它提供了一种可靠且适应性强的方法来管理表单状态、验证和提交。React Final Form 是用户友好且高效的，并为复杂场景提供高级功能。

### React Final Form 主要功能

- 声明式 API：React Final Form 采用声明式方法来定义表单的结构和行为。使用 React 组件，您可以轻松描述表单字段和验证规则，从而简化理解和维护。
- 表单状态管理：“最终表单状态”对象管理库中的表单状态。此状态包括表单字段、验证状态和已与之交互的字段的值。
- 验证：使用 React Final Form，您可以使用同步和异步验证来确保您的表单没有错误。为每个字段定义验证规则;任何错误将自动显示在用户界面中。
- 字段级控制：您可以精确控制每个表单字段，从访问单个字段值到检查验证错误和其他属性。
- 提交：管理表单提交是一个简单的过程。您需要创建一个提交函数，该函数将接收输入值，并且可以通过单击按钮或其他类似事件来激活。
- 表单渲染：使用 React Final Form，您可以选择呈现表单组件的方式。您不受外观限制，因此使您能够设计独特且个性化的表单布局。
- 性能优化：该库针对性能进行了优化，减少了不必要的重新渲染和更新，从而提高了应用程序的速度。
- 第三方组件：您可以毫不费力地将 React Final Form 与第三方库和组件合并，这使您能够利用众所周知的 UI 框架（如 Material-UI 或 Ant Design）进行表单输入。
- 可扩展性：该库具有高度灵活的插件系统，允许您根据自己的独特要求自定义和扩展其功能。

开始使用 React Final Form 时，您必须将其作为依赖项安装在项目中并导入所需的组件。然后，使用 JSX 语法定义表单，并利用提供的 props 和方法来管理表单交互。

### React Final Form 用法

以下是关于 React Final Form 的基本指南：

- 安装：首先安装必要的软件包：

```bash
npm install react-final-form final-form
```

- 创建一个表单组件：要使用 React Final Form 创建一个新的表单组件，你可以按照这个简单的例子：

```js
import React from 'react';
import { Form, Field } from 'react-final-form';

const MyForm = () => {
  const onSubmit = (values) => {
    console.log('Form values:', values);
  };

  const validate = (values) => {
    const errors = {};
    if (!values.firstName) {
      errors.firstName = 'Required';
    }
    if (!values.lastName) {
      errors.lastName = 'Required';
    }
    return errors;
  };

  return (
    <Form
      onSubmit={onSubmit}
      validate={validate}
      render={({ handleSubmit }) => (
        <form onSubmit={handleSubmit}>
          <div>
            <label>First Name</label>
            <Field name="firstName" component="input" type="text" />
          </div>
          <div>
            <label>Last Name</label>
            <Field name="lastName" component="input" type="text" />
          </div>
          <button type="submit">Submit</button>
        </form>
      )}
    />
  );
};

export default MyForm;
```

在此示例中，我们使用组件来包装表单，并使用 Form Field 组件来定义单个表单字段。

- 字段组件：组件 Field 定义表单字段。它具有各种内置组件（ input 、 textarea 、 select 等），或者您可以创建自定义组件。您还可以使用 meta prop 访问表单状态和验证信息。
- 验证：React Final Form 允许您定义验证函数来验证表单值。 Form 组件的 validate prop 接受一个验证函数，该函数返回带有验证错误的对象。
- 提交：使用 Form 组件时， onSubmit 道具应包含一个在提交表单时执行的功能。此函数可以处理表单提交、进行 API 调用或执行其他必要的操作。
- 初始值：您可以使用 Form 组件的 initialValues prop 为表单设置初始值。
- 表单状态：React Final Form 提供了一个 FormSpy 组件，允许您订阅和访问表单的状态，这对于更高级的方案很有帮助。
- 修饰器：可以使用修饰器增强窗体的功能，修饰器是可以修改窗体行为的高阶组件。
- 字段级验证：您可以通过将验证函数作为 prop 传递给 Field 组件来定义字段级验证。
- 提交和重置：您可以使用 Form 组件提供的 和 功能控制表单提交 submit 和 reset 重置。

以上是使用 React Final Form 的简单指南。该库提供了许多功能和自定义选项来管理复杂的应用程序表单。请参阅官方 React 最终表单文档以获取更全面的信息和示例。

## 总结

在 React 应用程序中构建表单时，像 Formik、React Hook Form 和 React Final Form 这样的库可以显著简化流程。每个库都有其特点和优势，可以满足各种项目要求和开发偏好。

当您将这些库添加到 React 项目中时，您可以简化表单创建，改善用户体验，并将更多时间用于开发创造性功能，而不是为复杂的表单设置而苦苦挣扎。

感谢您抽出宝贵时间阅读本文。我希望你发现它有帮助。祝您的编码工作好运！

[原文链接](https://dzone.com/articles/3-best-react-form-libraries) 本文由追马翻译校验
---
