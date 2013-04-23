
mongodb tool
***********************

**export**

- d: database
- c: collection
- o: output
- q: query

.. code-block:: bash

    mongoexport -d db -c collection -q '{"limit":100,"sort":[{"play":-1},{"atime":1}]}' -o board.json 


**import**

- d: database
- c: collection
- file: the file need to be imported 

.. code-block:: bash

    mongoimport -d db -c collection --file board.json 


