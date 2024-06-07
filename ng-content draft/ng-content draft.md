In the world of modern web development, building reusable and flexible components is crucial. Angular, provides a powerful feature known as **ng-content** to achieve this. This feature allows developers to project content from a parent component into a child component, making it easier to create dynamic and customizable components. In this blog post, we'll explore what **ng-content** is, how it works, and how you can use it to enhance your Angular applications.

**What is ng-content?**

**ng-content** is an Angular directive used for content projection, which is a technique that enables you to insert content from a parent component into a child component. This is particularly useful for creating reusable components where the content inside the component can be defined by the parent component.

**How Does ng-content Work?**

When you use **ng-content** in a child component, it acts as a placeholder. During runtime, Angular replaces this placeholder with the content passed from the parent component. This mechanism allows for greater flexibility and reusability of components.

**Basic Usage of ng-content**

Let’s start with a simple example to understand the basic usage of **ng-content**.

**Child Component (alert.component.html)**

    <div class="alert">
        <ng-content />
    </div>

**Parent Component** (**app.component.html**)

    <app-alert>
        <p>This is an important alert message!</p>
    </app-alert>

In this example, the **<ng-content></ng-content>** tag in the **alert.component.html** acts as a placeholder. The content within the **<app-alert>** tags in the **app.component.html** is projected into this placeholder, resulting in the following rendered HTML.

![A black box with white text

Description automatically generated](Aspose.Words.98aae1ac-46f8-4823-bca2-aadca379f2bc.003.png)

**Named Slots with ng-content**

Angular also allows for more complex content projection using named slots (select attiribute). Named slots enable you to define multiple placeholders within a single component, each of which can be filled with different content from the parent component.

**Child Component (card.component.html)**

![A computer screen with text on it

Description automatically generated](Aspose.Words.98aae1ac-46f8-4823-bca2-aadca379f2bc.004.png)

**Parent Component (app.component.html)![A black screen with white text

Description automatically generated](Aspose.Words.98aae1ac-46f8-4823-bca2-aadca379f2bc.005.png)**

**In this example, the select attribute in ng-content specifies which elements to project into each placeholder. The rendered HTML will look like this:**

![A screenshot of a computer

Description automatically generated](Aspose.Words.98aae1ac-46f8-4823-bca2-aadca379f2bc.006.png)

While all these were simple use cases of ng-content promoting re-usability, the true potential of ng-content is exposed when it is used with ng-template. 

In the following scenario there exists a card component which can show data of a student as well as a teacher. Let’s explore how we can re-use the same card component for showing the details of the teacher or the student without using conditionals like @if.

Let’s first see the student component.

**student-card.component.ts
![A screen shot of a computer program

Description automatically generated](Aspose.Words.98aae1ac-46f8-4823-bca2-aadca379f2bc.007.png)**

Now let’s see the teacher component.

**teacher-card.component.ts**

![A screen shot of a computer program

Description automatically generated](Aspose.Words.98aae1ac-46f8-4823-bca2-aadca379f2bc.008.png)

The interesting thing to notice here is the #rowRef template reference. We will read the reference in the child component.

Here is the child component which is card component.

![A screen shot of a computer program

Description automatically generated](Aspose.Words.98aae1ac-46f8-4823-bca2-aadca379f2bc.009.png)

Notice how the projected content from student card component and teacher card component is accessed via contentChild. In this case we get access to the template ‘rowRef’ passed from parent components. 

In this way we can show either the content of the teacher or the content of the student without passing @if and introducing any additional components or variables.
