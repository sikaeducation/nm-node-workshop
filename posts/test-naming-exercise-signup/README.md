---
questions:
  - id: 1
    prompt: |
      ```ts
      test("Name?", () => {
        const signupSpy = jest.fn()
        render(<SignUpForm signupHandler={signupSpy} />)

        const goodEmail = "good@email.com"
        const input = screen.getByRole("textbox")
        const button = screen.getByRole("button")

        type(input, goodEmail)
        click(button)

        const successMessage = screen.getByText("Congratulations!")

        expect(successMessage).toBeInTheDocument()
        expect(signupSpy).toHaveBeenCalled()
      })
      ```
    answer: |
      `<SignUpForm>` calls sign up handler and displays success message when given a valid email
  - id: 2
    prompt: |
      ```ts
      test("Name?", () => {
        const signupSpy = jest.fn()
        render(<SignUpForm signupHandler={signupSpy} />)

        const badEmail = "bad@email.com"
        const input = screen.getByRole("textbox")
        const button = screen.getByRole("button")

        type(input, badEmail)
        click(button)

        const errorMessage = screen.getByText("Oops!")

        expect(errorMessage).toBeInTheDocument()
        expect(signupSpy).not.toHaveBeenCalled()
      })
      ```
    answer: |
      `<SignUpForm>` displays failure message when given an invalid email
---

# Test Naming: Signup

_For a sign-up component where a user types their email address and clicks a button to be added to a mailing list, name the following tests using the style of your choice:_
