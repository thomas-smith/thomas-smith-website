---
title: Questionnaire Scrapper
date: 2017-11-23 05:35:33
---

This is a custom website scrapper for a task that I am currently undertaking at
work.

```JavaScript
if (JSON.parse(localStorage.getItem('questions')) === null) {
    // Find all yes radio buttons and auto click
    $("label:contains('Yes')").click();
    $("label:contains('No action points identified')").click();
    $('textarea').last().append('N/A');

    setTimeout(function() {
        var section = $('.breadcrumb-title').html();

        var q = [{
            'Company': $('.standard-breadcrumbs li:nth-child(5) span').html(),
            'Sections': []
        }];


        q[0]['Sections'].push({
            'section': $('.breadcrumb-title').html(),
            questions: []
        });

        $('.questionnaire-answers-section-question-options').each(function(ele) {
            q[0]['Sections'][0]['questions'].push({
                'Question': $(this).find('p').html(),
                'Answer': $(this).find('.question-answer-selected-text span:nth-child(2)').html(),
                'Resons': $(this).find('.question-answer-textanswered').html()
            })
        })

        localStorage.setItem('questions', JSON.stringify(q));
        $('.standard-submit').click();
    }, 200);

} else {
    // Find all yes radio buttons and auto click
    $("label:contains('Yes')").click();
    $("label:contains('No action points identified')").click();
    $('textarea').last().append('N/A');

    setTimeout(function() {
        var q = JSON.parse(localStorage.getItem('questions'));

        var nq = {
            'section': $('.breadcrumb-title').html(),
            'questions': []
        };

        $('.questionnaire-answers-section-question-options').each(function(ele) {

            nq['questions'].push({
                'Question': $(this).find('p').html(),
                'Answer': $(this).find('.question-answer-selected-text span:nth-child(2)').html(),
                'Resons': $(this).find('.question-answer-textanswered').html()
            })
        })

        q[0]['Sections'].push(nq);
        localStorage.setItem('questions', JSON.stringify(q));

        $('.standard-submit').click();
    }, 200)
}
```

```JavaScript
copy(JSON.parse(localStorage.getItem('questions')));
localStorage.clear();
```
