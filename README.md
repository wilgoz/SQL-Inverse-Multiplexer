# SQL-Inverse-Multiplexer
The project is proposed by a company called iCognition.

The objective of this project is to improve the functionality of an existing software (Content Manager, developed by MicroFocus), to allow the collation of results from multiple database instances, and return them through a single query within the CM software.

## Members
*   Donghoon Chang (u5342047@anu.edu.au)
*   Willy Ghozali (u6272951@anu.edu.au)
*   Rahil Vora (Rahil.Vora@anu.edu.au)
*   Scarlet Qin (Sijia.Qin@anu.edu.au)
*   Siddarth Thakur (Siddharth.Thakur@anu.edu.au)
*   Melissa Turner (u6350995@anu.edu.au)
*   Daniel Turner (u5562347@anu.edu.au)

## Solutions
We are required to develop software that intercepts calls from the Content Manager application and distribute those calls to all related databases.

To address this issue, multiple potential solutions have been made:
*   Developing a MiddleWare that interacts with both the CM and database server
*   DLL Injection
*   Designing an intermediate database that holds other related databases
*   SQL Proxy

It is important to note that the possibilities of these solutions are not definite.

## Resources
*   Content Manager SDK: <https://github.com/content-manager-sdk/Community>
*   TDS Bridge: <https://github.com/MindFlavor/TDSBridge>