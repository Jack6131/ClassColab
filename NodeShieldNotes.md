# Node Shield

## Summary
    Node Shields goal really isnt about fighting dependency confusion but more along the lines of stopping malware imported through NPM packages to not lead to security issues through the use of a CBOM and SBOM where they will limit the resources a specific library will have access to so they cannot exploit the flaw in node which allows the software to have full access to system resources. 

## Artifact
    https://github.com/KTH-LangSec/nodeshield

## npm flaws
    -Node Runs With Full Access to System Resources
    -Most Node Packages Rely On Other 3rd Party Node Packages Leading to Lard Dependency Chain

## Goal Of Node Shield
    - Control Dependency Hierarchy on what can and cannot be imported
    - Conditions For Node Shield To Work As Intended
        * Supply Chain of Node Shield isnt Compromised
        * SBOM Generator is not Compromised
        * NodeJS itself isnt Compromised
        * Javascript is limited to only evaluating/accesing variables within the current scope

## Questions
    Quote From Paper 
    ```
    Assumptions The security of NodeShield is predicated on thefollowing assumptions on JavaScript, Node.js, and the vm module.First, dynamic code
    evaluation in JavaScript is limited to accessingonly variables from the current scope—per the language specifica-tion [18]. Second, the only
    three ways to load modules in Node.js arethe require function (in CommonJS), the import syntax (in ESMod-ules), and the import function (both)
    —per the Node.js docs [ 20 ].Third, we assume the vm module 1) traps all uses of both the importsyntax and function, 2) prevents use of dynamic
    code evaluationAPIs and 3) provides a fresh JavaScript context without Node.js-specific built-ins or implicit access to variables from the
    contextin which it is instantiated—the former two are supported by theNode.js docs [20] while we empirically validate the latter.
    ```
    - It seems like the assumptions are a problem that another paper seems to answer which is the enforcing build steps to only access certain files and directories. I wonder if using this as an enforcment would allow for a more secure system for building code.