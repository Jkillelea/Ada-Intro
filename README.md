# Quick intro to Ada
Ada is a *statically* typed, compiled language with an emphasis on clarity, maintainability, and reliability.
Software written in Ada is known for being painful to develop and, when made right, never breaking. Ada runs on most modern computers and some microcontrollers. Its primary applications are in real time systems which require provably reliable software, such as avionics, high speed rail, and space vehicles.

## History
Ada is named after Ada Lovelace, one of the first computer programmers. It was created in response to a 1983 Department of Defense request for a programming language that would replace the hundreds the DoD used at the time. From 1983 to 1996, the DoD mandated the use of Ada in all of its software projects. However, it fell out of favor and not many people actually complied. The language has been updated since, with the most recent version being Ada 2012.

## Tooling
The only free compiler is named `gnat`, and can be installed with `sudo apt install -y gnat`. There is also an IDE called gnat-gps.

## Hello World

```ada
-- File hello_world.adb
with Ada.Text_IO;
procedure Hello_World is
begin
  Ada.Text_IO.Put_Line ("Hello World");
end Hello_World;
```

  - Line 1: Comments start with `--`
  - Line 2: `with Ada.Text_IO;`
    - This line introduces three things. First: libraries are imported with the `with` statement. The library is named `Ada.Text_IO`. Subpackages, functions, and components are separated with a period `.`. ADA IS NOT CASE SENSITIVE, but the convention is to name things with `Upper_Camel_Case` standards. Third all statements are terminated with a semicolon `;`.
  - Line 3:  `procedure Hello_World is`
    - Introduces a procedure named `Hello_World`. In Ada, a procedure is equivalent to a void function. In addition, there's no `Main` procedure required. A bare procedure like this  can be compiled and executed.
  - Line 4: `begin`
    - If we had variables, we would need to declare them between the words `is` and `begin`. Ada does not let variables be declared in the same block as executable code.
  - Line 5: `Ada.Text_IO.Put_Line ("Hello World");`
    - This calls the procedure `Put_Line` in the package `Ada.Text_IO`. `Put_Line` takes an argument of type `String`, which is a **fixed length** array of characters;
  - Line 6: `end Hello_World;`
    - This ends the block. Note that we name the block that's being ended, and a semicolon finishes the statement.

## Compile and Run
```bash
$ gnatmake hello_world.adb
$ ./hello_world
Hello World
```

`Gnatmake` does all the steps needed on simple projects. A build system called GPR is also available.

## The Simplest Program
This program does nothing

```ada
procedure Does_Nothing is
begin
  null;
end Does_Nothing;
```

Note that Ada requires us to explicitly say `null;`, so there's no ambiguity about whether we intended something to happen.
