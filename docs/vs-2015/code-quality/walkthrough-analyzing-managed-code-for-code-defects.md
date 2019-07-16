---
title: 'Przewodnik: Analizowanie kodu zarządzanego pod względem wad kodu | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d8412318efd2292fd0f5a0f0ef52fe36c7d06c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201146"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Przewodnik: Analizowanie kodu zarządzanego pod kątem błędów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku możesz analizować za pomocą narzędzia do analizy kodu zarządzanego projektu pod względem wad kodu.  
  
 W tym instruktażu będą krok po kroku przez proces przy użyciu analizy kodu, aby analizować swoje zestawy kodu zarządzanego na platformie .NET dla zapewnienia zgodności z wytycznymi programu Microsoft .NET Framework.  
  
 W tym przewodniku możesz:  
  
- Analizuj i popraw ostrzeżenia wady kodu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>Utwórz bibliotekę klas  
  
#### <a name="to-create-a-class-library"></a>Aby utworzyć bibliotekę klas  
  
1. Na **pliku** menu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], kliknij przycisk **New** a następnie kliknij przycisk **projektu**.  
  
2. W **nowy projekt** dialogowego **typów projektów**, kliknij przycisk **Visual C#** .  
  
3. W obszarze **szablony**, wybierz opcję **biblioteki klas**.  
  
4. W **nazwa** polu tekstowym **CodeAnalysisManagedDemo** a następnie kliknij przycisk **OK**.  
  
5. Po utworzeniu projektu otwórz plik Class1.cs.  
  
6. Zastąp istniejący tekst w Class1.cs z następującym kodem:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7. Zapisz plik Class1.cs.  
  
## <a name="analyze-the-project"></a>Analizowanie projektu  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Aby analizować zarządzanych projekt pod względem wad kodu  
  
1. Wybierz projekt CodeAnalysisManagedDemo **Eksploratora rozwiązań**.  
  
2. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
     Zostanie wyświetlona strona właściwości CodeAnalysisManagedDemo.  
  
3. Kliknij przycisk **analizy**.  
  
4. Upewnij się, że **Włącz analizę kodu podczas kompilacji (definiuje stałą CODE_ANALYSIS**) jest zaznaczone.  
  
5. Z **Uruchom ten zestaw reguł** listy rozwijanej wybierz **wszystkie reguły firmy Microsoft**.  
  
6. Na **pliku** menu, kliknij przycisk **Zapisz wybrane elementy**, a następnie zamknij ManagedDemo strony właściwości.  
  
7. Na **kompilacji** menu, kliknij przycisk **kompilacji ManagedDemo**.  
  
     Ostrzeżenia kompilacji projektu CodeAnalysisManagedDemo są zgłaszane w **analizy kodu** i **dane wyjściowe** systemu windows.  
  
     Jeśli **analizy kodu** okno nie jest widoczna, na **analizy** menu, wybierz **Windows** i następnie **wybierz analizy kodu**.  
  
## <a name="correct-the-code-analysis-issues"></a>Rozwiązać problemy dotyczące analizy kodu  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Aby poprawić naruszeń reguł analizy kodu  
  
1. Na **widoku** menu, kliknij przycisk **lista błędów**.  
  
     W zależności od wybranego profilu deweloper może być konieczne wskaż **Windows inne** na **widoku** menu, a następnie kliknij przycisk **lista błędów**.  
  
2. W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**.  
  
3. Następnie rozwiń węzeł właściwości, a następnie otwórz plik AssemblyInfo.cs.  
  
4. Aby poprawić ostrzeżenia, należy użyć następujących:  
  
- [CA1014: Oznacz zestawy atrybutem CLSCompliant](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: "pokaz" powinien być oznaczony atrybutem CLSCompliant, a jej wartość powinna być prawdziwe.  
  
  - Dodaj kod `using``System;` w pliku AssemblyInfo.cs.  
  
       Następnie dodaj ten kod `[assembly: CLSCompliant(true)]` -to-end w pliku AssemblyInfo.cs.  
  
       Skompiluj ponownie projekt.  
  
- [CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następującego konstruktora do klasy: demo(String) publiczne  
  
  - Dodaj Konstruktor `public demo (String s) : base(s) { }` do klasy `demo`.  
  
- [CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następującego konstruktora do klasy: Pokaz publiczny (String, wyjątku)  
  
  - Dodaj Konstruktor `public demo (String s, Exception e) : base(s, e) { }` do klasy `demo`.  
  
- [CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następującego konstruktora do klasy: chronione pokaz (SerializationInfo, StreamingContext)  
  
  - Dodaj kod `using System.Runtime.Serialization;` na początku pliku Class1.cs.  
  
       Następnie dodaj Konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       Skompiluj ponownie projekt.  
  
- [CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Dodaj następującego konstruktora do klasy: help.Start() publiczne  
  
  - Dodaj Konstruktor `public demo () : base() { }` do klasy `demo` **.**  
  
       Skompiluj ponownie projekt.  
  
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w wyrazie nazwę przestrzeni nazw "testCode" przez zmianę na "TestCode".  
  
  - Zmień wielkość liter w wyrazie przestrzeń nazw `testCode` do `TestCode`.  
  
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w wyrazie nazwy typu "pokaz" przez zmianę na "Pokaz".  
  
  - Zmień nazwę elementu członkowskiego do `Demo`.  
  
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Popraw wielkość liter w wyrazie name "elementu członkowskiego" przez zmianę na "Item".  
  
  - Zmień nazwę elementu członkowskiego do `Item`.  
  
- [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Zmień nazwę "testCode.demo" w celu w "Exception".  
  
  - Zmień nazwę klasy i jego konstruktorów do `DemoException`.  
  
- [CA2210: Zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Zaloguj się "ManagedDemo" kluczem silnej nazwy.  
  
  - Na **projektu** menu, kliknij przycisk **właściwości ManagedDemo**.  
  
       Właściwości projektu są wyświetlane.  
  
       Kliknij przycisk **podpisywania**.  
  
       Wybierz **Podpisz zestaw** pole wyboru.  
  
       W **wybierz plik klucza o nazwie ciąg** listy wybierz  **\<nowy... >** .  
  
       **Utwórz klucz silnej nazwy** pojawi się okno dialogowe.  
  
       W **nazwę pliku klucza**, wpisz TestKey.  
  
       Wprowadź hasło, a następnie kliknij przycisk **OK**.  
  
       Na **pliku** menu, kliknij przycisk **Zapisz wybrane elementy**, a następnie zamknij na stronach właściwości.  
  
       Skompiluj ponownie projekt.  
  
- [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Dodaj atrybut [Serializable] do typu "pokaz", ponieważ ten typ implementuje interfejs ISerializable.  
  
  - Dodaj `[Serializable ()]` do klasy atrybutu `demo`.  
  
       Skompiluj ponownie projekt.  
  
  Po zakończeniu zmiany pliku Class1.cs powinien wyglądać następująco:  
  
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
  
#### <a name="to-exclude-code-defect-warnings"></a>Aby wyłączyć ostrzeżenia wad kodu  
  
1. Dla każdej z pozostałych ostrzeżenia należy wykonać następujące czynności:  
  
   1. W oknie analizy kodu zaznacz ostrzeżenie.  
  
   2. Wybierz **akcje**, następnie wybierz **Pomiń komunikat**, a następnie wybierz **w pliku pominięć projektu**.  
  
      Aby uzyskać więcej informacji, zobacz [jak: Pomijanie ostrzeżeń przy użyciu elementu Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. Skompiluj ponownie projekt.  
  
    Projekt zostanie skompilowany bez żadnych ostrzeżeń ani błędów.
