---
title: 'Przewodnik: Analizowanie kodu zarządzanego pod kątem wad kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609333"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Wskazówki: analizowanie zarządzanego kodu pod względem wad kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu analizujesz zarządzany projekt pod kątem wad kodu za pomocą narzędzia do analizy kodu.

 Ten przewodnik przeprowadzi Cię przez proces korzystania z analizy kodu do analizowania zestawów kodu zarządzanego platformy .NET pod kątem zgodności z zaleceniami dotyczącymi projektowania Microsoft .NET Framework.

 W tym instruktażu zawarto następujące instrukcje:

- Analizowanie i poprawianie ostrzeżeń wad kodu.

## <a name="prerequisites"></a>Wymagania wstępne

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].,

## <a name="create-a-class-library"></a>Tworzenie biblioteki klas

#### <a name="to-create-a-class-library"></a>Aby utworzyć bibliotekę klas

1. W menu **plik** [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] kliknij pozycję **Nowy** , a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** w obszarze **typy projektów**kliknij pozycję **Wizualizacja C#** .

3. W obszarze **Szablony**wybierz pozycję **Biblioteka klas**.

4. W polu tekstowym **Nazwa** wpisz **CodeAnalysisManagedDemo** , a następnie kliknij przycisk **OK**.

5. Po utworzeniu projektu Otwórz plik Class1.cs.

6. Zastąp istniejący tekst w Class1.cs następującym kodem:

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Zapisz plik Class1.cs.

## <a name="analyze-the-project"></a>Analizowanie projektu

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Aby analizować projekt zarządzany pod kątem wad kodu

1. Wybierz projekt CodeAnalysisManagedDemo w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Właściwości**.

     Zostanie wyświetlona strona właściwości CodeAnalysisManagedDemo.

3. Kliknij pozycję **CodeAnalysis**.

4. Upewnij się, że jest zaznaczone pole wyboru **Włącz analizę kodu podczas kompilacji (zdefiniowano stałą CODE_ANALYSIS**).

5. Z listy rozwijanej **Uruchom ten zestaw reguł** wybierz pozycję **Microsoft wszystkie reguły**.

6. W menu **plik** kliknij polecenie **Zapisz wybrane elementy**, a następnie zamknij strony właściwości ManagedDemo.

7. W menu **kompilacja** kliknij pozycję **Kompiluj ManagedDemo**.

     Ostrzeżenia kompilacji projektu CodeAnalysisManagedDemo są raportowane w oknach **Analiza kodu** i **dane wyjściowe** .

     Jeśli okno **Analiza kodu** nie zostanie wyświetlone, w menu **Analizuj** wybierz pozycję **Windows** , a następnie **Wybierz pozycję Analiza kodu**.

## <a name="correct-the-code-analysis-issues"></a>Popraw problemy z analizą kodu

#### <a name="to-correct-code-analysis-rule-violations"></a>Aby poprawić naruszenia reguł analizy kodu

1. W menu **Widok** kliknij **Lista błędów**.

     W zależności od wybranego profilu dewelopera może zajść potrzeba wskaż **inne okna** w menu **Widok** , a następnie kliknąć przycisk **Lista błędów**.

2. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki**.

3. Następnie rozwiń węzeł właściwości, a następnie otwórz plik AssemblyInfo.cs.

4. Aby skorygować ostrzeżenia, użyj następującego:

- [CA1014: Oznacz zestawy za pomocą CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: "demonstracja" powinna być oznaczona przy użyciu CLSCompliantAttribute, a jego wartość powinna być równa true.

  - Dodaj `using``System;` kodu do pliku AssemblyInfo.cs.

       Następnie Dodaj kod `[assembly: CLSCompliant(true)]` na końcu pliku AssemblyInfo.cs.

       Ponownie skompiluj projekt.

- [CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Dodaj następujący Konstruktor do tej klasy: Demonstracja publiczna (ciąg)

  - Dodaj Konstruktor `public demo (String s) : base(s) { }` do klasy `demo`.

- [CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Dodaj następujący Konstruktor do tej klasy: Demonstracja publiczna (String, Exception)

  - Dodaj Konstruktor `public demo (String s, Exception e) : base(s, e) { }` do klasy `demo`.

- [CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Dodaj następujący Konstruktor do tej klasy: Prezentacja chroniona (SerializationInfo, StreamingContext)

  - Dodaj `using System.Runtime.Serialization;` kodu na początku pliku Class1.cs.

       Następnie Dodaj Konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Ponownie skompiluj projekt.

- [CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Dodaj następujący Konstruktor do tej klasy: pokaz publiczny ()

  - Dodaj Konstruktor `public demo () : base() { }` do klasy `demo` **.**

       Ponownie skompiluj projekt.

- [CA1709: Identyfikatory powinny mieć poprawną wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Name: Popraw wielkość liter w nazwie przestrzeni nazw "TestCode", zmieniając ją na "TestCode".

  - Zmień wielkość liter `testCode` przestrzeni nazw, aby `TestCode`.

- [CA1709: Identyfikatory powinny mieć poprawną wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Name: Popraw wielkość liter nazwy typu "demonstracyjna" przez zmianę na "demonstracja".

  - Zmień nazwę elementu członkowskiego na `Demo`.

- [CA1709: Identyfikatory powinny mieć poprawną wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Name: Popraw wielkość liter w nazwie elementu członkowskiego przez zmianę na "Item".

  - Zmień nazwę elementu członkowskiego na `Item`.

- [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Rename: Zmień nazwę "TestCode. demonstracyjna" na zakończenie "Exception".

  - Zmień nazwę klasy i jej konstruktorów na `DemoException`.

- [CA2210: zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Podpisz "ManagedDemo" kluczem o silnej nazwie.

  - W menu **projekt** kliknij polecenie **właściwości ManagedDemo**.

       Pojawią się właściwości projektu.

       Kliknij pozycję **podpisywanie**.

       Zaznacz pole wyboru **podpisz zestaw** .

       Z listy **Wybierz plik klucza nazwy ciągu** wybierz **\<New... >** .

       Zostanie wyświetlone okno dialogowe **Tworzenie klucza silnej nazwy** .

       W **Nazwa pliku klucza**wpisz TestKey.

       Wprowadź hasło, a następnie kliknij przycisk **OK**.

       W menu **plik** kliknij polecenie **Zapisz wybrane elementy**, a następnie zamknij strony właściwości.

       Ponownie skompiluj projekt.

- [CA2237: Oznacz typy ISerializable with SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: Dodaj atrybut [Serializable] do typu "demonstracji", ponieważ ten typ implementuje interfejs ISerializable.

  - Dodaj atrybut `[Serializable ()]` do klasy `demo`.

       Ponownie skompiluj projekt.

  Po wprowadzeniu zmian plik Class1.cs powinien wyglądać następująco:

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>Wyklucz ostrzeżenia analizy kodu

#### <a name="to-exclude-code-defect-warnings"></a>Aby wykluczyć ostrzeżenia defektu kodu

1. Dla każdego z pozostałych ostrzeżeń wykonaj następujące czynności:

   1. W oknie Analiza kodu wybierz ostrzeżenie.

   2. Wybierz pozycję **Akcje**, a następnie wybierz pozycję **Pomiń komunikat**, a następnie wybierz pozycję **plik pominięć projektu**.

      Aby uzyskać więcej informacji, zobacz [How to: pomijanie ostrzeżeń przy użyciu elementu menu.](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. Ponownie skompiluj projekt.

    Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.
