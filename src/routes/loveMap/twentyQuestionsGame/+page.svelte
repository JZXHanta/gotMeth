<script>
  /** @typedef {Object} Question
   * @property {string} question - the text of the question
   * @property {string[]} choices - available answer choices
   */

  /** @type {{ questions: Question[] }} */
  let twentyQuestions = {
    questions: [
      {
        question: "I can name my partners best friends.",
        choices: ["True", "False"],
      },
      {
        question:
          "I can tell you what stresses my partner is currently facing.",
        choices: ["True", "False"],
      },
      {
        question:
          "I know the names of some of the people who have been irritating my partner lately.",
        choices: ["True", "False"],
      },
      {
        question: "I can tell you some of my partners life dreams.",
        choices: ["True", "False"],
      },
      {
        question:
          "I am very familiar with my partner's religious beliefs and ideas.",
        choices: ["True", "False"],
      },
      {
        question: "I can tell you about my partner's basic philosophy of life.",
        choices: ["True", "False"],
      },
      {
        question: "I can list the relatives my partner likes the least.",
        choices: ["True", "False"],
      },
      {
        question: "I know my partner's favorite music.",
        choices: ["True", "False"],
      },
      {
        question: "I can list my partner's three favorite movies.",
        choices: ["True", "False"],
      },
      {
        question: "My spouse is familiar with my current stresses.",
        choices: ["True", "False"],
      },
      {
        question: "I know the three most special times in my partner's life.",
        choices: ["True", "False"],
      },
      {
        question:
          "I can tell you the most stressful thing that happened to my partner as a child.",
        choices: ["True", "False"],
      },
      {
        question:
          "I can list my partner's major hopes and aspirations in life.",
        choices: ["True", "False"],
      },
      {
        question: "I know my partner's major current worries.",
        choices: ["True", "False"],
      },
      {
        question: "My spouse know who my friends are.",
        choices: ["True", "False"],
      },
      {
        question:
          "I know what my partner would want to do if he or she suddenly won the lottery.",
        choices: ["True", "False"],
      },
      {
        question:
          "I can tell you in detail my first impressions of my partner.",
        choices: ["True", "False"],
      },
      {
        question:
          "Periodically I ask my partner about his or her world right now.",
        choices: ["True", "False"],
      },
      {
        question: "I feel that my partner knows me pretty well.",
        choices: ["True", "False"],
      },
      {
        question: "My spouse is familiar with my hopes and dreams.",
        choices: ["True", "False"],
      },
    ],
  };

  /** @type {number}*/
  let numberOfTrues = 0;

  /** @type {(string|null)[]} */
  let answers = Array(twentyQuestions.questions.length).fill(null);

  /** @type {number} */
  $: numberOfTrues = answers.filter((answer) => answer === "True").length;

  /**
   * Handles change in answer selection
   * @param {number} index
   * @param {string} value
   */
  function handleChange(index, value) {
    answers[index] = value;
  }
</script>

<h1>Twenty Questions Game</h1>
<p>
  By giving honest answers to the following questions, you will get a sense of
  the quality of your current love maps. For the most accurate reading of how
  your marriage is doing on this first principle, both of you should complete
  the following.
</p>
<p>Read each statement, and select true or false.</p>

{#each twentyQuestions.questions as question, index}
  <fieldset>
    <legend>{question.question}</legend>
    <div>
      {#each question.choices as choice}
        <input
          type="radio"
          id={`${question.question}-${choice}`}
          name={question.question}
          value={choice}
          on:change={() => handleChange(index, choice)}
        />
        <label for={`${question.question}-${choice}`}>{choice}</label>
      {/each}
    </div>
  </fieldset>
{/each}

<p><strong>Scoring:</strong> Give yourself a point for each true answer.</p>

<p>Number of True answers: {numberOfTrues}</p>

<p>
  <strong>10 or higher:</strong> This is an area of strength for your marriage. You
  4 have a fairly detailed map of your spouse's everyday life, hopes, fears, and
  dreams. You know what makes your spouse “tick.” Based on your score, you'll probably
  find the love map exercises that follow easy and gratifying. They will serve as
  a reminder of how connected you and your partner are. Try not to take for granted
  this knowledge and un-derstanding of each other. Keeping in touch in this way ensures
  you'll be well equipped to handle any problem areas that crop up in your relationship.
</p>

<p>
  <strong>Below 10:</strong> Your marriage could stand some improvement in this area.
  Perhaps you never had the time or the tools to really get to know each other. Or
  perhaps your love maps have become outdated as your lives have changed over the
  years. In either case, by taking the time to learn more about your spouse now,
  you'll find your relation-ship becomes stronger.
</p>
