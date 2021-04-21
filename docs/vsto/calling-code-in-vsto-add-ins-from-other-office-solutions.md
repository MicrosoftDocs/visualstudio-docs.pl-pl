---
title: Wywołanie kodu w dodatki VSTO z innych rozwiązań pakietu Office
description: Dowiedz się, jak można uwidocznić obiekt w dodatku VSTO dla innych rozwiązań, w tym Microsoft Office rozwiązań.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2519c9d1a22eb6f5577a258fb9b465cfd7caafc2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826983"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Wywołanie kodu w dodatki VSTO z innych rozwiązań pakietu Office
  Obiekt w dodatku VSTO można uwidocznić w innych rozwiązaniach, w tym w innych Microsoft Office rozwiązaniach. Jest to przydatne, jeśli dodatek VSTO udostępnia usługę, z której chcesz korzystać w innych rozwiązaniach. Jeśli na przykład masz dodatek VSTO dla programu Microsoft Office Excel, który wykonuje obliczenia na danych finansowych z usługi internetowej, inne rozwiązania mogą wykonać te obliczenia, wywołując dodatek VSTO programu Excel w czasie wykonywania.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Ten proces ma dwa główne kroki:

- W dodatku VSTO uwidocznij obiekt dla innych rozwiązań.

- W innym rozwiązaniu uzyskaj dostęp do obiektu udostępnianego przez dodatek VSTO i wywołaj elementy członkowskie obiektu.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Typy rozwiązań, które mogą wywołać kod w dodatku
 Obiekt w dodatku VSTO można uwidocznić dla następujących typów rozwiązań:

- Visual Basic for Applications (VBA) w dokumencie, który jest ładowany w tym samym procesie aplikacji co dodatek VSTO.

- Dostosowania na poziomie dokumentu, które są ładowane w tym samym procesie aplikacji co dodatek VSTO.

- Inne dodatki VSTO utworzone przy użyciu szablonów projektów pakietu Office w Visual Studio.

- Dodatki COM VSTO (czyli dodatki VSTO, które bezpośrednio implementują <xref:Extensibility.IDTExtensibility2> interfejs).

- Każde rozwiązanie działające w innym procesie niż dodatek VSTO (te typy rozwiązań są również nazywane klientami *poza procesem).* Należą do nich aplikacje, które automatyzują aplikację pakietu Office, takie jak Windows Forms lub aplikacja konsolowa, oraz dodatki VSTO, które są ładowane w innym procesie.

## <a name="expose-objects-to-other-solutions"></a>Udostępnianie obiektów innym rozwiązaniom
 Aby uwidocznić obiekt w dodatku VSTO dla innych rozwiązań, wykonaj następujące kroki w dodatku VSTO:

1. Zdefiniuj klasę, którą chcesz uwidocznić dla innych rozwiązań.

2. Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodę w `ThisAddIn` klasie . Zwraca wystąpienie klasy, które chcesz uwidocznić innym rozwiązaniom.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Definiowanie klasy, którą chcesz uwidocznić dla innych rozwiązań
 Klasa, którą chcesz uwidocznić, musi być co najmniej publiczna, musi mieć atrybut true i musi uwidaczniać interfejs <xref:System.Runtime.InteropServices.ComVisibleAttribute> [IDispatch.](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 

 Zalecanym sposobem uwidoczninia [interfejsu IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) jest wykonanie następujących kroków:

1. Zdefiniuj interfejs, który deklaruje elementy członkowskie, które mają być ujawniane innym rozwiązaniom. Ten interfejs można zdefiniować w projekcie dodatku VSTO. Można jednak zdefiniować ten interfejs w oddzielnym projekcie biblioteki klas, jeśli chcesz uwidocznić klasę dla rozwiązań innych niż VBA, aby rozwiązania wywołujące dodatek VSTO mogły odwoływać się do interfejsu bez odwoływania się do projektu dodatku VSTO.

2. Zastosuj atrybut <xref:System.Runtime.InteropServices.ComVisibleAttribute> do tego interfejsu i ustaw dla tego atrybutu wartość **true.**

3. Zmodyfikuj klasę, aby zaimplementować ten interfejs.

4. Zastosuj atrybut do klasy i ustaw ten atrybut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> na wartość **None** <xref:System.Runtime.InteropServices.ClassInterfaceType> wyliczenia.

5. Jeśli chcesz uwidocznić tę klasę klientom poza procesem, może być również konieczne:

   - Wyprowadz klasę z <xref:System.Runtime.InteropServices.StandardOleMarshalObject> klasy . Aby uzyskać więcej informacji, zobacz [Expose classes to out-of-process clients (Udostępnianie](#outofproc)klas klientom poza procesem).

   - Ustaw właściwość **register for COM interop** w projekcie, w którym definiujesz interfejs. Ta właściwość jest niezbędna tylko wtedy, gdy chcesz umożliwić klientom używanie wczesnego powiązania do wywołania dodatku VSTO.

   Poniższy przykład kodu demonstruje `AddInUtilities` klasę z `ImportData` metodą, która może być wywoływana przez inne rozwiązania. Aby zobaczyć ten kod w kontekście większego przewodnika, zobacz [Walkthrough: Call code in a VSTO Add-in from VBA (Przewodnik:](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)wywołanie kodu w dodatku VSTO z kodu VBA).

   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

### <a name="expose-classes-to-vba"></a>Uwidocznij klasy dla VBA
 W przypadku wykonania powyższych kroków kod VBA może wywołać tylko metody zadeklarowane w interfejsie. Kod VBA nie może wywołać żadnych innych metod w klasie, w tym metod, które klasa uzyskuje z klas bazowych, takich jak <xref:System.Object> .

 Możesz też uwidocznić [interfejs IDispatch,](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) ustawiając atrybut na wartość <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> AutoDispatch lub AutoDual <xref:System.Runtime.InteropServices.ClassInterfaceType> wyliczenia. Jeśli uwidocznisz interfejs, nie musisz deklarować metod w osobnym interfejsie. Jednak kod VBA może wywołać wszystkie metody publiczne i niestatyczne w klasie, w tym metody uzyskane z klas bazowych, takich jak <xref:System.Object> . Ponadto klienci poza procesem, którzy używają wczesnego powiązania, nie mogą wywołać klasy .

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Udostępnianie klas klientom poza procesem
 Jeśli chcesz uwidocznić klasę w dodatku VSTO dla klientów poza procesem, należy wyprowadzić klasę z klasy , aby upewnić się, że klienci poza procesem mogą wywołać uwidoczniony obiekt dodatku <xref:System.Runtime.InteropServices.StandardOleMarshalObject> VSTO. W przeciwnym razie próby uzyskania wystąpienia obiektu widocznego w kliencie poza procesem mogą nieoczekiwanie się nie powieść.

 Ten błąd wynika z tego, że wszystkie wywołania do modelu obiektów aplikacji pakietu Office muszą być wykonane w głównym wątku interfejsu użytkownika, ale wywołania z klienta poza procesem do obiektu zostaną przysłane do dowolnego wątku RPC (zdalnego wywołania procedury). Mechanizm marshalingu COM w .NET Framework nie przełączy wątków i zamiast tego podejmie próbę marshalingu wywołania do obiektu w przychodzącym wątku RPC, a nie głównym wątku interfejsu użytkownika. Jeśli obiekt jest wystąpieniem klasy, która pochodzi od klasy , wywołania przychodzące do obiektu są automatycznie marshaledowane do wątku, w którym został utworzony ujawniony obiekt, który będzie głównym wątkiem interfejsu użytkownika aplikacji <xref:System.Runtime.InteropServices.StandardOleMarshalObject> hosta.

 Aby uzyskać więcej informacji na temat używania wątków w rozwiązaniach pakietu Office, zobacz [Obsługa wątków w psłudze Office.](../vsto/threading-support-in-office.md)

### <a name="override-the-requestcomaddinautomationservice-method"></a>Zastąp metodę RequestComAddInAutomationService
 Poniższy przykład kodu pokazuje, jak zastąpić <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> w `ThisAddIn` klasie w dodatku VSTO. W przykładzie przyjęto założenie, że zdefiniowano klasę o nazwie `AddInUtilities` , którą chcesz uwidocznić dla innych rozwiązań. Aby zobaczyć ten kod w kontekście większego przewodnika, zobacz [Walkthrough: Call code in a VSTO Add-in from VBA (Przewodnik:](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)wywołanie kodu w dodatku VSTO z kodu VBA).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

 Po załadowaniu dodatku VSTO metoda [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodę . Środowisko uruchomieniowe przypisuje zwrócony obiekt do właściwości COMAddIn.Object obiektu reprezentującego dodatek <xref:Microsoft.Office.Core.COMAddIn> VSTO. Ten <xref:Microsoft.Office.Core.COMAddIn> obiekt jest dostępny dla innych rozwiązań pakietu Office i rozwiązań, które automatyzują pakiet Office.

## <a name="access-objects-from-other-solutions"></a>Uzyskiwanie dostępu do obiektów z innych rozwiązań
 Aby wywołać obiekt ujawniony w dodatku VSTO, wykonaj następujące kroki w rozwiązaniu klienta:

1. Pobierz obiekt <xref:Microsoft.Office.Core.COMAddIn> reprezentujący ujawniony dodatek VSTO. Klienci mogą uzyskać dostęp do wszystkich dostępnych dodatków VSTO przy użyciu właściwości w modelu obiektów aplikacji `Application.COMAddIns` pakietu Office hosta.

2. Uzyskaj dostęp do właściwości COMAddIn.Object <xref:Microsoft.Office.Core.COMAddIn> obiektu . Ta właściwość zwraca obiekt ujawniony z dodatku VSTO.

3. Wywołaj elementy członkowskie widocznego obiektu.

   Sposób używania wartości zwracanej właściwości COMAddIn.Object różni się w przypadku klientów VBA i klientów innych niż VBA. W przypadku klientów poza procesem jest konieczny dodatkowy kod, aby uniknąć sytuacji wyścigu.

### <a name="access-objects-from-vba-solutions"></a>Uzyskiwanie dostępu do obiektów z rozwiązań VBA
 W poniższym przykładzie kodu pokazano, jak używać VBA do wywołania metody udostępnianej przez dodatek VSTO. To makro VBA wywołuje metodę o nazwie , która jest zdefiniowana w dodatku VSTO o `ImportData` nazwie **ExcelImportData**. Aby zobaczyć ten kod w kontekście większego przewodnika, zobacz [Walkthrough: Call code in a VSTO Add-in from VBA (Przewodnik:](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)wywołanie kodu w dodatku VSTO z kodu VBA).

```vb
Sub CallVSTOMethod()
    Dim addIn As COMAddIn
    Dim automationObject As Object
    Set addIn = Application.COMAddIns("ExcelImportData")
    Set automationObject = addIn.Object
    automationObject.ImportData
End Sub
```

### <a name="access-objects-from-non-vba-solutions"></a>Uzyskiwanie dostępu do obiektów z rozwiązań innych niż VBA
 W rozwiązaniu innym niż VBA należy rzutować wartość właściwości COMAddIn.Object na interfejs, który implementuje, a następnie wywołać metody widoczne dla obiektu interfejsu. W poniższym przykładzie kodu pokazano, jak wywołać metodę z innego dodatku narzędzi VSTO, który został utworzony przy użyciu narzędzi deweloperycznych pakietu Office w `ImportData` Visual Studio.

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

 W tym przykładzie, jeśli spróbujesz rzutować wartość właściwości COMAddIn.Object na klasę, a nie na interfejs, kod zrzuci `AddInUtilities` `IAddInUtilities` element <xref:System.InvalidCastException> .

## <a name="see-also"></a>Zobacz też
- [Program VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)
- [Przewodnik: wywołanie kodu w dodatku VSTO z VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
