---
title: "PDF Templates Generate Attachment Links"
date: "July 5, 2021"
category: "Product Update"
source_url: "https://www.xurrent.com/product-updates/pdf-templates-generate-attachment-links"
slug: "pdf-templates-generate-attachment-links"
---

# PDF Templates Generate Attachment Links

When an approval task for a change or project is assigned to its approvers, Xurrent generates a separate approval summary for the recipients.  This summary is attached as a PDF file to the email notification and is also available in the task itself when an approver opens it.

The information that is included in these summary PDFs can be customized in the ‘[PDF Designs](https://www.xurrent.com/product-updates/pdf-designs)’ section of the Settings console.  Account administrators and account designers can edit these default designs.  They can also add more designs so that a different design can be used for specific approval tasks.  It is even possible to empty the PDF design field to ensure that a change or project summary PDF does not get generated for some approval tasks.

What has changed is that the default PDF designs for the ‘Change Summary’ and ‘Project Summary’ now include links to the files that are attached to changes or projects.  This means that approvers will be able to open these attachments from their change or project summary.

Approvers can use the hyperlinks in their summary PDF to open attachments for 1 week without having to log in.  After 1 week, approvers need to log in to Xurrent before they can retrieve an attachment.

These updated PDF designs are immediately available for new accounts.  Account administrators and account designers of existing accounts can add download links to change and project summaries by adding a code snippet to the Notes section of the HTML design.  After editing, this section could look like this:

`{{if change.notes.length}}
<section>
<h2>Notes</h2>
<div class="without-label">
{{for change.notes}}
<div class="note">
<div class="note-header">
<div class="person">{{:person.name}}</div>
<div class="date">{{:created_at}}</div>
</div>
{{:html}}

{{if attachments.length}}
<div class="attachments">
{{for attachments}}
<div class="attachment">
<a href="{{:url}}">{{:name}}</a>
</div>
{{/for}}
</div>
{{/if}}
</div>
{{/for}}
</div>
</section>
{{/if}}`
