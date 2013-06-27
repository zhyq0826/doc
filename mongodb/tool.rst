mongodb tool
***********************

**export**

- d: database
- c: collection
- o: output
- q: query

.. code-block:: bash

    mongoexport -d db -c collection -q '{"limit":100,"sort":[{"play":-1},{"atime":1}]}' -o board.json 
    
    mongoexport -d androidesk_aniv -c ask --csv -f q,item,a,imgid,fobjs,vfobjs,atime   -q '{}' -o ask.cvs 



**import**

- d: database
- c: collection
- file: the file need to be imported 

.. code-block:: bash

    mongoimport -d db -c collection --file board.json 
    
    


