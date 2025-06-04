# AP Calculus Exam Files

This directory contains AP Calculus AB exam PDFs that are displayed on the Practice Problems page.

## File Structure

```
public/exams/
├── 2017/
│   ├── ap-calculus-ab-2017-international-practice-exam-mcq.pdf
│   ├── ap-calculus-ab-2017-international-practice-exam-mcq-answers.pdf
│   ├── ap-calculus-ab-2017-international-practice-exam-frq.pdf
│   └── ap-calculus-ab-2017-international-practice-exam-frq-scoring-guidelines.pdf
├── 2018/
│   └── (add 2018 exam files here)
└── 2019/
    └── (add 2019 exam files here)
```

## Adding New Exam Files

To add new exam files:

1. **Create year directory** (if it doesn't exist):
   ```bash
   mkdir public/exams/YYYY
   ```

2. **Add PDF files** with the naming convention:
   - Multiple Choice Questions: `ap-calculus-ab-YYYY-*-mcq.pdf`
   - MCQ Answer Key: `ap-calculus-ab-YYYY-*-mcq-answers.pdf`
   - Free Response Questions: `ap-calculus-ab-YYYY-*-frq.pdf`
   - FRQ Scoring Guidelines: `ap-calculus-ab-YYYY-*-frq-scoring-guidelines.pdf`

3. **Update the practice.vue file** to include the new year in the `examFiles` object:
   ```javascript
   const examFiles = ref({
     // ... existing years
     'YYYY': {
       'mcq': '/exams/YYYY/ap-calculus-ab-YYYY-*-mcq.pdf',
       'mcq-answers': '/exams/YYYY/ap-calculus-ab-YYYY-*-mcq-answers.pdf',
       'frq': '/exams/YYYY/ap-calculus-ab-YYYY-*-frq.pdf',
       'frq-answers': '/exams/YYYY/ap-calculus-ab-YYYY-*-frq-scoring-guidelines.pdf'
     }
   });
   ```

## File Requirements

- **Format**: PDF files only
- **Accessibility**: Files must be publicly accessible (in the public directory)
- **Naming**: Follow the convention shown above for automatic detection
- **Size**: Keep file sizes reasonable for web viewing (under 10MB recommended)

## Supported Exam Types

- **MCQ**: Multiple Choice Questions
- **MCQ Answers**: Answer key for multiple choice questions
- **FRQ**: Free Response Questions
- **FRQ Answers**: Scoring guidelines and solutions for free response questions

## Browser Compatibility

The PDF viewer works with modern browsers that support inline PDF viewing. For browsers that don't support this feature, fallback options (open in new tab, download) are provided.
