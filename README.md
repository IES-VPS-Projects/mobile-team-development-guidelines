<p align="center"><image src="images/logo-white.png" ></p>
<p  align="center"><b>Intelligent</b></p>
<p align="center"><i>We design and build advanced security technology</i></p>



> The global security environment is fast changing and more challenging than it has ever been, knowing what new threats may arise is key for governments in their mandate as guarantor of public safety and security. It is critical for them to have the agility to take adequate steps, pro-actively as well as reactively. Lack of information however is not the problem, rather information overload and information contained in silos; thus, critical pieces needed to complete the picture are never brought together. Our Security Ecosystem consists of products that are purpose built to address these challenges ground up. They are powerful, open and co-operative, creating an extraordinary eco-system that enables intelligence led policing.

---

# Intelligent Flutter Development Guidelines
In this repository, we have collated the important Flutter best practices that should be kept in mind for application development. 

These guidelines should be followed by every member of the mobile team to ensure good quality code and performance of the applications.

# Sections
 + Philosophy
   > Write what you need and no more, but when you write it, do it right.
Avoid implementing features you don’t need. You can’t design a feature without knowing what the constraints are. Implementing features "for completeness" results in unused code that is expensive to maintain, learn about, etc.

 + <a href="guidelines/documentation.md">Documentation</a>
    *  <a href="guidelines/documentation.md##avoid-useless-documentations">Avoid useless documentation</a>
 + <a href="guidelines/code_pattern.md">Code Pattern</a> 
   * <a href="guidelines/formatting.md">Formatting</a>
      * <a href="guidelines/formatting.md#use-spread-collections">Use spread collections</a>
      * <a href="guidelines/formatting.md#use-if-condition-instead-of-conditional-expression">Use if condition instead of conditional expression</a>
          * <a href="guidelines/formatting.md#exception">Exception</a>

           * <a href="guidelines/formatting.md#employ-early-return">Employ early `return`</a>


      * <a href="guidelines/formatting.md#use-cascades-operator">Use cascades Operator</a>
      * <a href="guidelines/formatting.md#use-asyncawait-overusing-futures-callback">Use async/await overusing futures callback</a>
      * <a href="guidelines/formatting.md#use-of-const">Use of `const`</a>
      * <a href="guidelines/formatting.md#avoid-using-as-instead-use-is-operator">Avoid using `as` instead use `is` operator</a>
      * <a href="guidelines/formatting.md#avoid-lines-longer-than-80-characters">Avoid lines longer than 80 characters</a>
      * <a href="guidelines/formatting.md#indent-multi-line-argument-and-parameter-lists-by-2-characters">Indent multi-line argument and parameter lists by 2 characters</a>
      * <a href="guidelines/formatting.md#always-declare-return-types#always-declare-return-type">Always declare return types</a>

      * <a href="guidelines/formatting.md#always-declare-return-types#always-declare-return-type">White spaces</a>

   * <a href="guidelines/widget_structure.md"> Widget styling</a> 
      * <a href="guidelines/widget_structure.md#split-widgets-into-sub-widgets"> Split widgets into sub Widgets</a> 
      * <a href="guidelines/widget_structure.md#use-raw-string"> Use raw string</a> 
      * <a href="guidelines/widget_structure.md#use-const-in-widgets"> Use `const` in Widgets</a> 
      * <a href="guidelines/widget_structure.md#use-interpolation-to-compose-strings"> Use interpolation to compose strings</a> 
      
   * <a href="guidelines/null_checks.md"> Nullability</a> 
      * <a href="guidelines/null_checks.md#lazy-instantiation"> Lazy instantiation (late)</a> 
      * <a href="guidelines/null_checks.md#Use--and--operators"> Use `??` and `?.` operators</a> 
      * <a href="guidelines/null_checks.md#dont-explicitly-initialize-variables"> Don’t explicitly initialize variables</a>  
   
   *  <a href="guidelines/logging.md">Logging</a>  
      * <a href="guidelines/logging.md#avoid-print-calls">Avoid `print()` calls</a>  
   
   
 + <a href="guidelines/naming_conventions.md">Naming Conventions</a>
   *  <a href="guidelines/naming_conventions.md# UpperCamelCase">Upper camel case</a>
   *  <a href="guidelines/naming_conventions.md#lower-case">Lower case</a>   
   *  <a href="guidelines/naming_conventions.md#lower-camelcase">Lower camel case</a>
   *  <a href="guidelines/naming_conventions.md#file-and-directory-naming">File and directory naming</a>   
   *  <a href="guidelines/naming_conventions.md#naming-consistency">Naming consistency</a> 
   *  <a href="guidelines/naming_conventions.md#variable-naming">Avoid short forms</a>    

 +  <a href="guidelines/state_management_separation_of_logic.md">State Management</a>      
    
 + <a href="guidelines/packages.md">Packages</a>
   * <a href="guidelines/packages.md#imports-formatting">Imports formatting</a>
   * <a href="guidelines/packages.md#do-name-import-prefixes-using-lowercase_with_underscores">Do name import prefixes using lowercase_with_underscores</a>
   * <a href="guidelines/packages.md#do-specify-exports-in-a-separate-section-after-all-imports">Do specify exports in a separate section after all imports</a>
 + <a href="guidelines/lint_rules.md">Lint Rules</a>
  

 + <a href="guidelines/testing.md"> Testing</a>
   * <a href="guidelines/unit_test.md">Unit test</a>
   * <a href="guidelines/intergration_test.md">Intergation test</a>
   * <a href="guidelines/widget_test.md">Widget test</a>
   * <a href="guidelines/test_sample.md">Sample test</a>
   * <a href="guidelines/test_resources.md">Resources</a>
  
## Author
 Eric Muli ,
 Mobile Engineer,
 Intelligent



