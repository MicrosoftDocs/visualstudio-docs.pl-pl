---
title: Instruktaż Analizowanie kodu zarządzanego pod kątem wad kodu | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ab1e0b890d6241742770ed38ff61fc1c2c0ed2f4
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535702"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Wskazówki: aby znaleźć wady kodu, użyj statycznej analizy kodu

W tym instruktażu analizujesz zarządzany projekt pod kątem wad kodu przy użyciu starszej analizy kodu.

Ten artykuł przeprowadzi Cię przez proces korzystania z starszej analizy w celu przeanalizowania zestawów kodu zarządzanego platformy .NET pod kątem zgodności z zaleceniami dotyczącymi projektowania platformy .NET.

## <a name="create-a-class-library"></a>Tworzenie biblioteki klas

1. Otwórz program Visual Studio i Utwórz nowy projekt na podstawie szablonu **biblioteki klas (.NET Framework)** .

1. Nazwij projekt **CodeAnalysisManagedDemo**.

1. Po utworzeniu projektu Otwórz plik *Class1.cs* .

1. Zastąp istniejący tekst w Class1.cs następującym kodem:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Zapisz plik Class1.cs.

## <a name="analyze-the-project-for-code-defects"></a>Analizowanie projektu pod kątem wad kodu

1. Wybierz projekt CodeAnalysisManagedDemo w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Właściwości**.

   Zostanie wyświetlona strona właściwości CodeAnalysisManagedDemo.

3. Wybierz kartę **Analiza kodu** .

::: moniker range="vs-2017"

4. Upewnij się, że wybrano **opcję Włącz analizę kodu podczas kompilacji** .

5. Z listy rozwijanej **Uruchom ten zestaw reguł** wybierz pozycję **Microsoft wszystkie reguły**.

::: moniker-end

::: moniker range=">=vs-2019"

4. Upewnij się, że w sekcji **analizatory binarne** jest wybrana wartość **Uruchom przy kompilacji** .

5. Z listy rozwijanej **aktywne reguły** wybierz pozycję **Microsoft wszystkie reguły**.

::: moniker-end

6. W menu **plik** kliknij polecenie **Zapisz wybrane elementy**, a następnie zamknij strony właściwości.

7. W menu **kompilacja** kliknij pozycję **Kompiluj CodeAnalysisManagedDemo**.

    Ostrzeżenia kompilacji projektu CodeAnalysisManagedDemo są wyświetlane w oknach **Lista błędów** i **danych wyjściowych** .

## <a name="correct-the-code-analysis-issues"></a>Popraw problemy z analizą kodu

1. W menu **Widok** wybierz **Lista błędów**.

    W zależności od wybranego profilu dewelopera może zajść potrzeba wskaż **inne okna** w menu **Widok** , a następnie wybierz **Lista błędów**.

1. W **Eksplorator rozwiązań**wybierz opcję **Pokaż wszystkie pliki**.

1. Rozwiń węzeł właściwości, a następnie otwórz plik *AssemblyInfo.cs* .

1. Poniższe porady umożliwiają poprawienie ostrzeżeń:

   [CA1014: Oznacz zestawy za pomocą CLSCompliantAttribute](../code-quality/ca1014.md): dodaj kod `[assembly: CLSCompliant(true)]` na końcu pliku AssemblyInfo.cs.

   [CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032.md): dodaj Konstruktor `public demo (String s) : base(s) { }` do klasy `demo`.

   [CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032.md): dodaj Konstruktor `public demo (String s, Exception e) : base(s, e) { }` do klasy `demo`.

   [CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032.md): dodaj Konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` do demonstracyjnej klasy. Należy również dodać instrukcję `using` dla <xref:System.Runtime.Serialization?displayProperty=fullName>.

   [CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032.md): dodaj Konstruktor `public demo () : base() { }` do klasy `demo`.

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709.md): Zmień wielkość liter w przestrzeni nazw `testCode` na `TestCode`.

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709.md): Zmień nazwę elementu członkowskiego na `Demo`.

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709.md): Zmień nazwę elementu członkowskiego na `Item`.

   [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710.md): Zmień nazwę klasy i jej konstruktorów na `DemoException`.

   [CA2237: Oznacz typy ISerializable z SerializableAttribute](../code-quality/ca2237.md): dodaj atrybut `[Serializable ()]` do klasy `demo`.

   [CA2210: zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210.md): Podpisz "CodeAnalysisManagedDemo" kluczem o silnej nazwie:

   1. W menu **projekt** wybierz pozycję **Właściwości CodeAnalysisManagedDemo**.

      Pojawią się właściwości projektu.

   1. Wybierz kartę **podpisywanie** .

   1. Zaznacz pole wyboru **podpisz zestaw** .

   1. Z listy **Wybierz plik klucza nazwy ciągu** wybierz pozycję **\<New >** .

      Zostanie wyświetlone okno dialogowe **Tworzenie klucza silnej nazwy** .

   1. W obszarze **Nazwa pliku klucza**wprowadź **TestKey**.

   1. Wprowadź hasło, a następnie wybierz przycisk **OK**.

   1. W menu **plik** wybierz polecenie **Zapisz wybrane elementy**, a następnie zamknij strony właściwości.

   Po zakończeniu wszystkich zmian plik Class1.cs powinien wyglądać następująco:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Ponownie skompiluj projekt.

## <a name="exclude-code-analysis-warnings"></a>Wyklucz ostrzeżenia analizy kodu

1. Dla każdego z pozostałych ostrzeżeń wykonaj następujące czynności:

    1. Wybierz ostrzeżenie w **Lista błędów**.

    1. W menu rozwijanym prawym przyciskiem myszy (menu kontekstowe) wybierz opcję **pomijaj** > **w pliku pomijania**.

1. Ponownie skompiluj projekt.

     Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.

## <a name="see-also"></a>Zobacz także

[Analiza kodu zarządzanego](../code-quality/code-analysis-for-managed-code-overview.md)
