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
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548000"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Przewodnik: Użyj statycznej analizy kodu, aby znaleźć wady kodu

W tym instruktażu analizujesz zarządzany projekt pod kątem wad kodu przy użyciu starszej analizy kodu.

Ten artykuł przeprowadzi Cię przez proces korzystania z starszej analizy w celu przeanalizowania zestawów kodu zarządzanego platformy .NET pod kątem zgodności z zaleceniami dotyczącymi projektowania platformy .NET.

## <a name="create-a-class-library"></a>Tworzenie biblioteki klas

### <a name="to-create-a-class-library"></a>Aby utworzyć bibliotekę klas

1. Na **pliku** menu, wybierz **New** > **projektu**.

1. W oknie dialogowym **Nowy projekt** rozwiń pozycję **zainstalowana** > **Wizualizacja C#** , a następnie wybierz pozycję **Windows Desktop**.

1. Wybierz szablon **Biblioteka klas (.NET Framework)** .

1. W polu tekstowym **Nazwa** wpisz **CodeAnalysisManagedDemo** , a następnie kliknij przycisk **OK**.

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

## <a name="analyze-the-project"></a>Analizowanie projektu

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Aby analizować projekt zarządzany pod kątem wad kodu

1. Wybierz projekt CodeAnalysisManagedDemo w **Eksplorator rozwiązań**.

1. W menu **projekt** kliknij polecenie **Właściwości**.

     Zostanie wyświetlona strona właściwości CodeAnalysisManagedDemo.

1. Wybierz kartę **Analiza kodu** .

1. Upewnij się, że jest zaznaczona opcja **Włącz analizę kodu podczas kompilacji** .

1. Z listy rozwijanej **Uruchom ten zestaw reguł** wybierz pozycję **Microsoft wszystkie reguły**.

1. W menu **plik** kliknij polecenie **Zapisz wybrane elementy**, a następnie zamknij strony właściwości.

1. W menu **kompilacja** kliknij pozycję **Kompiluj CodeAnalysisManagedDemo**.

    Ostrzeżenia kompilacji projektu CodeAnalysisManagedDemo są wyświetlane w oknach **Lista błędów** i **danych wyjściowych** .

## <a name="correct-the-code-analysis-issues"></a>Popraw problemy z analizą kodu

### <a name="to-correct-code-analysis-rule-violations"></a>Aby poprawić naruszenia reguł analizy kodu

1. W menu **Widok** wybierz **Lista błędów**.

    W zależności od wybranego profilu dewelopera może zajść potrzeba wskaż **inne okna** w menu **Widok** , a następnie wybierz **Lista błędów**.

1. W **Eksplorator rozwiązań**wybierz opcję **Pokaż wszystkie pliki**.

1. Rozwiń węzeł właściwości, a następnie otwórz plik *AssemblyInfo.cs* .

1. Poniższe porady umożliwiają poprawienie ostrzeżeń:

   [CA1014 Oznacz zestawy atrybutem](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)CLSCompliantAttribute: Microsoft. Design: element "demonstracyjn" powinien być oznaczony przy użyciu CLSCompliantAttribute, a jego wartość powinna być równa true.

   1. Dodaj kod `using System;` do pliku AssemblyInfo.cs.

   1. Następnie Dodaj kod `[assembly: CLSCompliant(true)]` na końcu pliku AssemblyInfo.cs.

   [CA1032: Zaimplementuj standardowe konstruktory](../code-quality/ca1032-implement-standard-exception-constructors.md)wyjątków: Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: Demonstracja publiczna (ciąg)

   1. Dodaj konstruktora `public demo (String s) : base(s) { }` do klasy `demo`.

   [CA1032: Zaimplementuj standardowe konstruktory](../code-quality/ca1032-implement-standard-exception-constructors.md)wyjątków: Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: Demonstracja publiczna (String, Exception)

   1. Dodaj konstruktora `public demo (String s, Exception e) : base(s, e) { }` do klasy `demo`.

   [CA1032: Zaimplementuj standardowe konstruktory](../code-quality/ca1032-implement-standard-exception-constructors.md)wyjątków: Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: Demonstracja chroniona (SerializationInfo, StreamingContext)

   1. Dodaj kod `using System.Runtime.Serialization;` na początku pliku Class1.cs.

   1. Następnie Dodaj Konstruktor`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Zaimplementuj standardowe konstruktory](../code-quality/ca1032-implement-standard-exception-constructors.md)wyjątków: Microsoft.Design: Dodaj następujący Konstruktor do tej klasy: pokaz publiczny ()

   1. Dodaj konstruktora `public demo () : base() { }` do klasy **.** `demo`

   [CA1709: Identyfikatory powinny mieć prawidłową](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)wielkość liter: Microsoft. nazewnictwo: Popraw wielkość liter w nazwie przestrzeni nazw "testCode", zmieniając ją na "TestCode".

   1. Zmień wielkość liter w przestrzeni nazw `testCode` na `TestCode`.

   [CA1709: Identyfikatory powinny mieć prawidłową](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)wielkość liter: Microsoft. nazewnictwo: Popraw wielkość liter w nazwie typu "demonstracja", zmieniając ją na "demonstracja".

   1. Zmień nazwę elementu członkowskiego na `Demo`.

   [CA1709: Identyfikatory powinny mieć prawidłową](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)wielkość liter: Microsoft. nazewnictwo: Popraw wielkość liter w nazwie elementu członkowskiego, zmieniając ją na "Item".

   1. Zmień nazwę elementu członkowskiego na `Item`.

   [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. nazewnictwo: Zmień nazwę pliku "testCode. demonstracyjna" na "Exception".

   1. Zmień nazwę klasy i jej konstruktorów na `DemoException`.

   [CA2210: Zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Podpisz element "CodeAnalysisManagedDemo" kluczem o silnej nazwie.

   1. W menu **projekt** wybierz pozycję **Właściwości CodeAnalysisManagedDemo**.

      Pojawią się właściwości projektu.

   1. Wybierz kartę podpisywanie.

   1. Zaznacz pole wyboru **podpisz zestaw** .

   1. Z listy **Wybierz plik klucza nazwy ciągu** wybierz pozycję  **\<nowy... >** .

      Zostanie wyświetlone okno dialogowe **Tworzenie klucza silnej nazwy** .

   1. W **Nazwa pliku klucza**wpisz TestKey.

   1. Wprowadź hasło, a następnie wybierz przycisk **OK**.

   1. W menu **plik** wybierz polecenie **Zapisz wybrane elementy**, a następnie zamknij strony właściwości.

   [CA2237 Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Dodaj atrybut [Serializable] do typu "demonstracja", ponieważ ten typ implementuje interfejs ISerializable.

   1. Dodaj atrybut do klasy `demo`. `[Serializable ()]`

   Po wprowadzeniu zmian plik Class1.cs powinien wyglądać następująco:

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

    1. W menu rozwijanym prawym przyciskiem myszy (menu kontekstowe > ) wybierz opcję Pomijaj**w pliku pomijania**.

1. Ponownie skompiluj projekt.

     Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.

## <a name="see-also"></a>Zobacz także

[Analiza kodu zarządzanego](../code-quality/code-analysis-for-managed-code-overview.md)