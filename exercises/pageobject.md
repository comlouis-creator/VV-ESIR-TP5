## Page Object Model

The image below shows the poll page of the [Simba Organizer](https://github.com/barais/doodlestudent/) application discussed in classes.

![Simba Organizer Poll page](simba-poll-page.png)

Write in this document the interface of a page object class for this page.

## Answer

class PollPage {
  // Navigates to the Poll page.//
  navigateTo()

  // Gets the current number of votes for the given option.//
  getOptionVotes(option: string): number

  // Clicks on the given option.//
  clickOption(option: string)

  // Clicks on the "Submit" button.//
  clickSubmit()

  // Gets the text of the success message that is displayed after submitting a vote.//
  getSuccessMessage(): string

  // Gets the text of the error message that is displayed when trying to submit a vote without selecting an option.//
  getErrorMessage(): string
}
