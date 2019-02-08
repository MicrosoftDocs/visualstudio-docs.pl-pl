---
title: Przewodnik analizowanie kodu zarządzanego pod względem wad kodu | Dokumentacja firmy Microsoft
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3097e52f99f044257b8eaf634455bdf19978d0c3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952844"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Przewodnik: Analizowanie kodu zarządzanego pod względem wad kodu

W tym przewodniku będzie analizować zarządzanego projektu pod względem wad kodu za pomocą narzędzia analizy kodu.

Ten przewodnik przeprowadzi Cię przez proces przy użyciu analizy kodu, aby analizować swoje zestawy kodu zarządzanego na platformie .NET dla zapewnienia zgodności z wytycznymi projektowania Microsoft .NET Framework.

## <a name="create-a-class-library"></a>Utwórz bibliotekę klas

### <a name="to-create-a-class-library"></a>Aby utworzyć bibliotekę klas

1. Na **pliku** menu, wybierz **New** > **projektu**.

1. W **nowy projekt** okna dialogowego rozwiń **zainstalowane** > **Visual C#** , a następnie wybierz **pulpitu Windows**.

1. Wybierz **biblioteki klas (.NET Framework)** szablonu.

1. W **nazwa** polu tekstowym **CodeAnalysisManagedDemo** a następnie kliknij przycisk **OK**.

1. Po utworzeniu projektu otwórz *Class1.cs* pliku.

1. Zastąp istniejący tekst w Class1.cs z następującym kodem:

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

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Aby analizować zarządzanych projekt pod względem wad kodu

1. Wybierz projekt CodeAnalysisManagedDemo **Eksploratora rozwiązań**.

1. Na **projektu** menu, kliknij przycisk **właściwości**.

     Zostanie wyświetlona strona właściwości CodeAnalysisManagedDemo.

1. Wybierz **analizy kodu** kartę.

1. Upewnij się, że **Włącz analizę kodu podczas kompilacji** jest zaznaczone.

1. Z **Uruchom ten zestaw reguł** listy rozwijanej wybierz **wszystkie reguły firmy Microsoft**.

1. Na **pliku** menu, kliknij przycisk **Zapisz wybrane elementy**, a następnie zamknij na stronach właściwości.

1. Na **kompilacji** menu, kliknij przycisk **kompilacji CodeAnalysisManagedDemo**.

    Ostrzeżenia kompilacji projektu CodeAnalysisManagedDemo są wyświetlane w **lista błędów** i **dane wyjściowe** systemu windows.

## <a name="correct-the-code-analysis-issues"></a>Rozwiązać problemy dotyczące analizy kodu

### <a name="to-correct-code-analysis-rule-violations"></a>Aby poprawić naruszeń reguł analizy kodu

1. Na **widoku** menu, wybierz **lista błędów**.

    W zależności od wybranego profilu deweloper może być konieczne wskaż **Windows inne** na **widoku** menu, a następnie wybierz **lista błędów**.

1. W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki**.

1. Rozwiń węzeł właściwości, a następnie otwórz *AssemblyInfo.cs* pliku.

1. Skorzystaj z następujących porad, aby poprawić ostrzeżenia:

   [CA1014: Oznacz zestawy atrybutem CLSCompliant](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: "pokaz" powinien być oznaczony atrybutem CLSCompliant, a jej wartość powinna być prawdziwe.

   1. Dodaj kod `using System;` w pliku AssemblyInfo.cs.

   1. Następnie dodaj ten kod `[assembly: CLSCompliant(true)]` -to-end w pliku AssemblyInfo.cs.

   [CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następującego konstruktora do klasy: demo(String) publiczne

   1. Dodaj Konstruktor `public demo (String s) : base(s) { }` do klasy `demo`.

   [CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następującego konstruktora do klasy: Pokaz publiczny (String, wyjątku)

   1. Dodaj Konstruktor `public demo (String s, Exception e) : base(s, e) { }` do klasy `demo`.

   [CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następującego konstruktora do klasy: chronione pokaz (SerializationInfo, StreamingContext)

   1. Dodaj kod `using System.Runtime.Serialization;` na początku pliku Class1.cs.

   1. Następnie dodaj Konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następującego konstruktora do klasy: help.Start() publiczne

   1. Dodaj Konstruktor `public demo () : base() { }` do klasy `demo` **.**

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w wyrazie nazwę przestrzeni nazw "testCode" przez zmianę na "TestCode".

   1. Zmień wielkość liter w wyrazie przestrzeń nazw `testCode` do `TestCode`.

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w wyrazie nazwy typu "pokaz" przez zmianę na "Pokaz".

   1. Zmień nazwę elementu członkowskiego do `Demo`.

   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w wyrazie name "elementu członkowskiego" przez zmianę na "Item".

   1. Zmień nazwę elementu członkowskiego do `Item`.

   [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Zmień nazwę "testCode.demo" w celu w "Exception".

   1. Zmień nazwę klasy i jego konstruktorów do `DemoException`.

   [CA2210: Zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Zaloguj się "CodeAnalysisManagedDemo" kluczem silnej nazwy.

   1. Na **projektu** menu, wybierz **właściwości CodeAnalysisManagedDemo**.

      Właściwości projektu są wyświetlane.

   1. Wybierz **podpisywanie** kartę.

   1. Wybierz **Podpisz zestaw** pole wyboru.

   1. W **wybierz plik klucza o nazwie ciąg** listy wybierz  **\<nowy... >**.

      **Utwórz klucz silnej nazwy** pojawi się okno dialogowe.

   1. W **nazwę pliku klucza**, wpisz TestKey.

   1. Wprowadź hasło, a następnie wybierz **OK**.

   1. Na **pliku** menu, wybierz **Zapisz wybrane elementy**, a następnie zamknij na stronach właściwości.

   [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Dodaj atrybut [Serializable] do typu "pokaz", ponieważ ten typ implementuje interfejs ISerializable.

   1. Dodaj `[Serializable ()]` do klasy atrybutu `demo`.

   Po zakończeniu zmiany pliku Class1.cs powinien wyglądać następująco:

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

1. Skompiluj ponownie projekt.

## <a name="exclude-code-analysis-warnings"></a>Wyklucz ostrzeżenia analizy kodu

1. Dla każdej z pozostałych ostrzeżenia należy wykonać następujące czynności:

    1. Wybrać ostrzeżenie w **lista błędów**.

    1. Z menu podręcznego (menu kontekstowe) wybierz **Pomiń** > **w pliku pominięć**.

1. Skompiluj ponownie projekt.

     Projekt zostanie skompilowany bez żadnych ostrzeżeń ani błędów.

## <a name="see-also"></a>Zobacz także

[Analiza kodu dla kodu zarządzanego](../code-quality/code-analysis-for-managed-code-overview.md)