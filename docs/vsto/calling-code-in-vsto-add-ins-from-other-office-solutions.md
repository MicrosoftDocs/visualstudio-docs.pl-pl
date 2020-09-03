---
title: Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 584406098f058c17b3dd215dda9c8c4e9498cf46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255326"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office
  Można uwidocznić obiekt w dodatku VSTO dla innych rozwiązań, w tym innych rozwiązań Microsoft Office. Jest to przydatne, jeśli dodatek narzędzi VSTO udostępnia usługę, która umożliwia korzystanie z innych rozwiązań. Na przykład jeśli masz dodatek narzędzi VSTO dla programu Microsoft Office Excel, który wykonuje obliczenia dotyczące danych finansowych z usługi sieci Web, inne rozwiązania mogą wykonywać te obliczenia przez wywołanie dodatku VSTO programu Excel w czasie wykonywania.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 W tym procesie istnieją dwa główne kroki:

- W dodatku VSTO Uwidocznij obiekt dla innych rozwiązań.

- W innym rozwiązaniu, uzyskuj dostęp do obiektu uwidocznionego przez dodatek VSTO i Wywołaj elementy członkowskie obiektu.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Typy rozwiązań, które mogą wywołać kod w dodatku
 Można uwidocznić obiekt w dodatku VSTO do następujących typów rozwiązań:

- Kod Visual Basic for Applications (VBA) w dokumencie, który jest ładowany w ramach tego samego procesu aplikacji co dodatek narzędzi VSTO.

- Dostosowania na poziomie dokumentu, które są ładowane w ramach tego samego procesu aplikacji co dodatek narzędzi VSTO.

- Inne dodatki narzędzi VSTO utworzone przy użyciu szablonów projektu pakietu Office w programie Visual Studio.

- Dodatki narzędzi VSTO dla modelu COM (czyli dodatki narzędzi VSTO, które implementują <xref:Extensibility.IDTExtensibility2> interfejs bezpośrednio).

- Każde rozwiązanie działające w innym procesie niż dodatek VSTO (te typy rozwiązań są również nazywane *klientami poza procesem*). Są to aplikacje automatyzujące automatyzację aplikacji pakietu Office, takie jak Windows Forms lub Aplikacja konsolowa, a także dodatki narzędzi VSTO, które są ładowane w innym procesie.

## <a name="expose-objects-to-other-solutions"></a>Uwidacznianie obiektów do innych rozwiązań
 Aby uwidocznić obiekt w dodatku VSTO dla innych rozwiązań, wykonaj następujące kroki w dodatku VSTO:

1. Zdefiniuj klasę, którą chcesz uwidocznić dla innych rozwiązań.

2. Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodę w `ThisAddIn` klasie. Zwróć wystąpienie klasy, które chcesz uwidocznić dla innych rozwiązań.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Zdefiniuj klasę, którą chcesz uwidocznić dla innych rozwiązań
 Co najmniej Klasa, którą chcesz uwidocznić musi być publiczna, musi mieć <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut ustawiony na **wartość true**i musi uwidaczniać Interfejs [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) .

 Zalecanym sposobem uwidocznienia interfejsu [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) jest wykonanie następujących czynności:

1. Zdefiniuj interfejs, który deklaruje członków, którzy mają być narażeni na inne rozwiązania. Ten interfejs można zdefiniować w projekcie dodatku VSTO. Można jednak zdefiniować ten interfejs w osobnym projekcie biblioteki klas, jeśli chcesz uwidocznić klasę w rozwiązaniach innych niż VBA, tak aby rozwiązania wywołujące dodatek VSTO mogły odwoływać się do interfejsu bez odwoływania się do projektu dodatku VSTO.

2. Zastosuj <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut do tego interfejsu i ustaw dla tego atrybutu **wartość true**.

3. Zmodyfikuj klasę, aby zaimplementować ten interfejs.

4. Zastosuj <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut do klasy i ustaw dla tego atrybutu wartość **Brak** w <xref:System.Runtime.InteropServices.ClassInterfaceType> wyliczeniu.

5. Jeśli chcesz uwidocznić tę klasę na klientach pozaprocesowych, może być również konieczne wykonanie następujących czynności:

   - Utwórz klasę z <xref:System.Runtime.InteropServices.StandardOleMarshalObject> . Aby uzyskać więcej informacji, zobacz [udostępnianie klas do klientów pozaprocesowych](#outofproc).

   - Ustaw właściwość **Zarejestruj dla międzyoperacyjności modelu COM** w projekcie, w którym został zdefiniowany interfejs. Ta właściwość jest konieczna tylko wtedy, gdy klienci mają używać wczesnego wiązania do wywołania dodatku VSTO.

   Poniższy przykład kodu demonstruje `AddInUtilities` klasę z `ImportData` metodą, która może być wywoływana przez inne rozwiązania. Aby wyświetlić ten kod w kontekście większego przewodnika, zobacz [Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

### <a name="expose-classes-to-vba"></a>Uwidacznianie klas w języku VBA
 Po wykonaniu powyższych kroków kod VBA może wywoływać tylko metody zadeklarowane w interfejsie. Kod języka VBA nie może wywoływać żadnych innych metod w klasie, w tym metod pobieranych przez klasę z klas bazowych, takich jak <xref:System.Object> .

 Możesz Alternatywnie uwidocznić Interfejs [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) przez ustawienie <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu na wartość autowysyłania lub autopodwójność <xref:System.Runtime.InteropServices.ClassInterfaceType> wyliczenia. Jeśli udostępnisz interfejs, nie musisz deklarować metod w osobnym interfejsie. Jednak kod języka VBA może wywoływać wszystkie metody publiczne i niestatyczne w klasie, włącznie z metodami uzyskanymi z klas bazowych, takich jak <xref:System.Object> . Ponadto klienci poza procesem, którzy używają wczesnego wiązania, nie mogą wywołać klasy.

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Uwidacznianie klas na klientach pozaprocesowych
 Jeśli chcesz uwidocznić klasę w dodatku VSTO na klientach pozaprocesowych, należy utworzyć klasę z, <xref:System.Runtime.InteropServices.StandardOleMarshalObject> Aby upewnić się, że klienci poza procesem mogą wywołać uwidoczniony obiekt dodatku VSTO. W przeciwnym razie próby pobrania wystąpienia uwidocznionego obiektu w nieoczekiwanym kliencie mogą niespodziewanie działać.

 Ten błąd jest spowodowany tym, że wszystkie wywołania do modelu obiektowego aplikacji pakietu Office muszą być wykonane w głównym wątku interfejsu użytkownika, ale wywołania z klienta pozaprocesowego do obiektu będą docierać do dowolnego wątku RPC (zdalnego wywołania procedury). Mechanizm kierujący modelem COM w .NET Framework nie będzie przełączać wątków i zamiast głównego wątku interfejsu użytkownika będzie podejmować próby skierowania wywołania do obiektu. Jeśli obiekt jest wystąpieniem klasy, która pochodzi od <xref:System.Runtime.InteropServices.StandardOleMarshalObject> , wywołania przychodzące do obiektu są automatycznie przekazywane do wątku, w którym został utworzony uwidoczniony obiekt, który będzie głównym wątkiem interfejsu użytkownika aplikacji hosta.

 Aby uzyskać więcej informacji o korzystaniu z wątków w rozwiązaniach pakietu Office, zobacz [Obsługa wątków w pakiecie Office](../vsto/threading-support-in-office.md).

### <a name="override-the-requestcomaddinautomationservice-method"></a>Zastąp metodę RequestComAddInAutomationService
 Poniższy przykład kodu demonstruje sposób przesłonięcia <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> w `ThisAddIn` klasie w dodatku narzędzi VSTO. W przykładzie przyjęto założenie, że zdefiniowano klasę o nazwie `AddInUtilities` , która ma zostać ujawniona dla innych rozwiązań. Aby wyświetlić ten kod w kontekście większego przewodnika, zobacz [Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

 Po załadowaniu dodatku VSTO [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> Metoda wywołuje metodę. Środowisko uruchomieniowe przypisuje zwracany obiekt do właściwości COMAddIn. Object <xref:Microsoft.Office.Core.COMAddIn> obiektu, który reprezentuje dodatek narzędzi VSTO. Ten <xref:Microsoft.Office.Core.COMAddIn> obiekt jest dostępny dla innych rozwiązań pakietu Office oraz rozwiązań, które automatyzują pakiet Office.

## <a name="access-objects-from-other-solutions"></a>Dostęp do obiektów z innych rozwiązań
 Aby wywołać uwidoczniony obiekt w dodatku VSTO, wykonaj następujące kroki w rozwiązaniu klienta:

1. Pobierz <xref:Microsoft.Office.Core.COMAddIn> obiekt reprezentujący uwidoczniony dodatek narzędzi VSTO. Klienci mogą uzyskać dostęp do wszystkich dostępnych dodatków narzędzi VSTO przy użyciu `Application.COMAddIns` właściwości w modelu obiektów aplikacji pakietu Office hosta.

2. Dostęp do właściwości COMAddIn. Object <xref:Microsoft.Office.Core.COMAddIn> obiektu. Ta właściwość zwraca uwidoczniony obiekt z dodatku VSTO.

3. Wywołaj członków uwidocznionego obiektu.

   Sposób używania wartości zwracanej właściwości COMAddIn. Object jest różny dla klientów języka VBA i klientów innych niż VBA. W przypadku klientów pozaprocesowych dodatkowy kod jest konieczny, aby uniknąć możliwego warunku wyścigu.

### <a name="access-objects-from-vba-solutions"></a>Dostęp do obiektów z rozwiązań VBA
 Poniższy przykład kodu demonstruje, jak używać języka VBA do wywołania metody, która jest udostępniona przez dodatek narzędzi VSTO. To makro języka VBA wywołuje metodę o nazwie `ImportData` , która jest zdefiniowana w dodatku VSTO o nazwie **ExcelImportData**. Aby wyświetlić ten kod w kontekście większego przewodnika, zobacz [Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

```vb
Sub CallVSTOMethod()
    Dim addIn As COMAddIn
    Dim automationObject As Object
    Set addIn = Application.COMAddIns("ExcelImportData")
    Set automationObject = addIn.Object
    automationObject.ImportData
End Sub
```

### <a name="access-objects-from-non-vba-solutions"></a>Dostęp do obiektów z rozwiązań innych niż VBA
 W rozwiązaniu innym niż VBA należy rzutować wartość właściwości COMAddIn. Object na interfejs, który implementuje, a następnie wywołać metody uwidocznione w obiekcie interfejsu. Poniższy przykład kodu demonstruje sposób wywołania `ImportData` metody z innego dodatku VSTO, który został utworzony przy użyciu narzędzi deweloperskich pakietu Office w programie Visual Studio.

```vb
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _
    addIn.Object, ExcelImportData.IAddInUtilities)
utilities.ImportData()
```

```csharp
object addInName = "ExcelImportData";
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;
utilities.ImportData();
```

 W tym przykładzie, jeśli spróbujesz rzutować wartość właściwości COMAddIn. Object na `AddInUtilities` klasę zamiast `IAddInUtilities` interfejsu, kod zgłosi <xref:System.InvalidCastException> .

## <a name="see-also"></a>Zobacz też
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
