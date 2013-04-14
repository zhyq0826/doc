doctype
-----------------

A proper Doctype which triggers standards mode in your browser should always be used. Quirks mode should always be avoided.
For simplicity we will use the html5 doctype, which is easy to remember.

.. code-block:: bash
    
    <!DOCTYPE html>

HTML Guidelines
------------------

*Paragraphs of text should always be placed in a <p> tag. Never use multiple <br/> tags.

*Items in list form should always be in <ul>, <ol>, or <dl>, Never a set of <div> or <p>

*Every form input that has text attached should utilize a <label> tag. Especially radio or checkbox elements.

*Even though quotes around attributes is optional, always put quotes around attributes for readability.

.. code-block:: bash

    <p class="line note" data-attribute="106">This is my paragraph of special text.</p>

*Make use of <thead>, <tfoot>, <tbody>, and <th> tags (and Scope attribute) when appropriate. (note: <tfoot> goes above <tbody> for speed reasons. You want the browser to load the footer before a table full of data.)

.. code-block:: bash

    <table summary="This is a chart of invoices for 2011.">
      <thead>
        <tr>
          <th scope="col">Table header 1</th>
          <th scope="col">Table header 2</th>
        </tr>
      </thead>
      <tfoot>
        <tr>
          <td>Table footer 1</td>
          <td>Table footer 2</td>
        </tr>
      </tfoot>
      <tbody>
        <tr>
          <td>Table data 1</td>
          <td>Table data 2</td>
        </tr>
      </tbody>
    </table>