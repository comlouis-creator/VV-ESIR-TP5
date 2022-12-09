## Find a bug

Clone the [Simba Organizer repository](https://github.com/barais/doodlestudent/) and follow the instructions to run the application on your machine.

Find a bug in the application. 

With the help of Selenium and the Page Object Model desing pattern write a simple test that fails for this bug.

Optionally make a pull request to the project.

Include in this document the code of the test and, if you did it, the link to the pull request.

## Answer

import { PollPage } from "./poll-page";

describe("Poll page", () => {
  let pollPage: PollPage;

  beforeEach(() => {
    pollPage = new PollPage();
    pollPage.navigateTo();
  });

  it("displays the correct number of votes for each option", () => {
    // Click on the first option.
    pollPage.clickOption("Option 1");

    // Submit the vote.
    pollPage.clickSubmit();

    // Assert that the number of votes for the selected option is correct.
    expect(pollPage.getOptionVotes("Option 1")).toBe(1);
  });
});

