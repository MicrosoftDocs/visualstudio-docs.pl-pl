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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c347000d75beb628c01c5a8f8275d4755db776f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910272"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office
  Obiekt można ujawnić w dodatku narzędzi VSTO dla programów do innych rozwiązań, w tym inne rozwiązania Microsoft Office. Jest to przydatne, jeśli dodatku narzędzi VSTO dla programów udostępnia usługę, aby włączyć innych rozwiązań do użycia. Na przykład jeśli masz dodatku narzędzi VSTO dla programu Microsoft Office Excel wykonuje obliczenia na dane finansowe z usługi sieci Web, innych rozwiązań wykonać te obliczenia za pośrednictwem wywołania do dodatku narzędzi VSTO dla programu Excel w czasie wykonywania.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Istnieją dwa podstawowe kroki w ramach tego procesu:  
  
-   W dodatku narzędzi VSTO dla programów należy udostępnić obiekt, do innych rozwiązań.  
  
-   W rozwiązaniu innym uzyskać dostęp do obiektu, udostępnianych przez usługi dodatku narzędzi VSTO dla programów i wywołanie elementów członkowskich obiektu.  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Typy rozwiązań, które można wywołać kodu w dodatku  
 Można udostępnić obiektu w dodatku narzędzi VSTO dla następujących typów rozwiązań:  
  
-   Kod Visual Basic for Applications (VBA) w dokumencie, który jest ładowany w tym samym procesie aplikacji jako dodatku narzędzi VSTO dla programów.  
  
-   Dostosowania na poziomie dokumentu, które są ładowane w tym samym procesie aplikacji jako dodatku narzędzi VSTO dla programów.  
  
-   Innych dodatków narzędzi VSTO utworzone przy użyciu szablonów projektów pakietu Office w programie Visual Studio.  
  
-   Dodatki narzędzi VSTO dla modelu COM (czyli dodatków narzędzi VSTO, które implementują <xref:Extensibility.IDTExtensibility2> bezpośrednio interfejsu).  
  
-   Wszystkie rozwiązania, które działa w ramach innego procesu niż dodatku narzędzi VSTO dla programów (tego rodzaju rozwiązania są również nazywane *klientów spoza procesu*). Obejmują one aplikacje, które automatyzują aplikacji pakietu Office, takich jak formularze Windows lub konsoli aplikacji i dodatków narzędzi VSTO dla programów, które są ładowane w ramach innego procesu.  
  
## <a name="expose-objects-to-other-solutions"></a>Udostępnianie obiektów do innych rozwiązań  
 Aby udostępnić obiektu w dodatku narzędzi VSTO dla programów do innych rozwiązań, wykonaj następujące kroki w dodatku VSTO:  
  
1.  Definiowanie klasy, która ma zostać uwidoczniona do innych rozwiązań.  
  
2.  Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> method in Class metoda `ThisAddIn` klasy. Zwraca wystąpienie klasy, którą chcesz udostępnić innych rozwiązań.  
  
### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Definiowanie klasy, którą chcesz udostępnić innych rozwiązań  
 Jako minimum, klasy, którą chcesz uwidocznić muszą być publiczne, musi on mieć <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną wartość atrybutu **true**, i musi uwidaczniać [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interfejsu.  
  
 Zalecanym sposobem udostępnienia [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interfejsu jest wykonaj następujące czynności:  
  
1. Zdefiniuj interfejs, który deklaruje elementów członkowskich, które chcesz udostępnić innych rozwiązań. Ten interfejs można zdefiniować w projekcie dodatku narzędzi VSTO. Można zdefiniować w projekcie osobnej klasy biblioteki tego interfejsu, jeśli chcesz udostępnić klasy na rozwiązania innych VBA tak, aby rozwiązania, które wywołują dodatku narzędzi VSTO dla programów może odwoływać się interfejs bez odwołania do projektu dodatku narzędzi VSTO.  
  
2. Zastosuj <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutu dla tego interfejsu, a następnie ustaw ten atrybut **true**.  
  
3. Zmodyfikuj klasy do zaimplementowania tego interfejsu.  
  
4. Zastosuj <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutów do klasy, a następnie ustaw ten atrybut **Brak** wartość <xref:System.Runtime.InteropServices.ClassInterfaceType> wyliczenia.  
  
5. Jeśli chcesz udostępnić tej klasy, aby klienci spoza procesu, konieczne może wykonać następujące czynności:  
  
   -   Pochodną klasy z <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Aby uzyskać więcej informacji, zobacz [ujawnić klasy klientom spoza procesu](#outofproc).  
  
   -   Ustaw **Zarejestruj dla współdziałania COM** właściwość w projekcie, w której definiujesz interfejsu. Ta właściwość jest tylko, jeśli chcesz umożliwić klientom na używanie wczesne powiązania do wywołania w dodatku narzędzi VSTO.  
  
   Poniższy przykład kodu demonstruje `AddInUtilities` klasy `ImportData` metodę, która może być wywoływany przez inne rozwiązania. Aby wyświetlić ten kod w kontekście większych wskazówki, zobacz [instruktażu: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="expose-classes-to-vba"></a>Udostępnianie klas z VBA  
 Po wykonaniu powyższych kroków, kod VBA można wywołać metody, które można zadeklarować w interfejsie. Kod VBA nie można wywołać wszelkich innych metod w klasie, włączając w to metody, które klasy uzyskuje klas podstawowych, takich jak <xref:System.Object>.  
  
 Alternatywnie można udostępnić [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interfejsu, ustawiając <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu wartości wiązaniem AutoDispatch lub elementu <xref:System.Runtime.InteropServices.ClassInterfaceType> wyliczenia. Należy udostępnić interfejs, nie trzeba zadeklarować metody w oddzielnych interfejsu. Jednak kod VBA można wywoływać żadnych metod publicznych i niestatycznych w klasie, włączając w to metody uzyskany z klas podstawowych, takich jak <xref:System.Object>. Ponadto klientów poza procesem, którzy używają wczesne powiązania nie można wywołać klasy.  
  
###  <a name="outofproc"></a> Udostępnianie klas klientom spoza procesu  
 Jeśli chcesz udostępnić klasy w dodatku narzędzi VSTO dla programów klientom spoza procesu utworzeniu klasy pochodnej klasy z <xref:System.Runtime.InteropServices.StandardOleMarshalObject> aby upewnić się, czy klienci spoza procesu może wywołać narażonych obiektu dodatku narzędzi VSTO. W przeciwnym razie próbuje pobrać wystąpienie obiektu uwidocznione w kliencie spoza procesu mogą nieoczekiwanie ulegają awarii.  
  
 Ten błąd jest, ponieważ wszystkie wywołania modelu obiektów w aplikacji pakietu Office, musi nastąpić w głównym wątku interfejsu użytkownika, ale wywołania z klienta spoza procesu do obiektu zostaną dostarczone dla dowolnego wątku (zdalne wywołania procedur) RPC. Mechanizm organizowania COM w .NET Framework nie przełączy się wątków, a zamiast tego będzie podejmować próby kierować wywołanie do obiektu na przychodzący wątek RPC zamiast głównego wątku interfejsu użytkownika. Jeśli obiekt jest wystąpieniem klasy, która jest pochodną <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, przychodzące wywołania do obiektu są automatycznie przekazywane do wątku, gdzie został utworzony obiekt narażonych, będzie główny wątek interfejsu użytkownika w aplikacji hosta.  
  
 Aby uzyskać więcej informacji o używaniu wątków w rozwiązaniach pakietu Office, zobacz [Obsługa wątkowości w Office](../vsto/threading-support-in-office.md).  
  
### <a name="override-the-requestcomaddinautomationservice-method"></a>Zastąp metodę RequestComAddInAutomationService  
 Poniższy przykład kodu demonstruje sposób zastąpienia <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> w `ThisAddIn` klasy w dodatku VSTO. W przykładzie założono, że zdefiniowano klasę o nazwie `AddInUtilities` , którą chcesz udostępnić innych rozwiązań. Aby wyświetlić ten kod w kontekście większych wskazówki, zobacz [instruktażu: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 Gdy dodatku narzędzi VSTO dla programów jest ładowany, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołania <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. Środowisko uruchomieniowe przypisuje zwracany obiekt z właściwością COMAddIn.Object <xref:Microsoft.Office.Core.COMAddIn> obiekt, który reprezentuje dodatku narzędzi VSTO dla programów. To <xref:Microsoft.Office.Core.COMAddIn> obiekt jest dostępny do innych rozwiązań pakietu Office i rozwiązania, które automatyzują pakietu Office.  
  
## <a name="access-objects-from-other-solutions"></a>Uzyskiwanie dostępu do obiektów z innych rozwiązań  
 Aby wywołać obiekt narażonych w dodatku narzędzi VSTO dla programów, należy wykonać następujące kroki w rozwiązaniu klienta:  
  
1. Pobierz <xref:Microsoft.Office.Core.COMAddIn> obiekt, który reprezentuje narażonych dodatku narzędzi VSTO. Klienci mogą uzyskiwać dostęp do wszystkich dostępnych dodatków narzędzi VSTO dla programów przy użyciu `Application.COMAddIns` właściwości w modelu obiektu hosta aplikacji pakietu Office.  
  
2. Dostęp do właściwości COMAddIn.Object <xref:Microsoft.Office.Core.COMAddIn> obiektu. Ta właściwość zwraca obiekt narażonych z dodatku narzędzi VSTO.  
  
3. Wywołaj członków narażonych obiektu.  
  
   Sposób, że używasz zwracana wartość właściwości COMAddIn.Object różni się dla klientów VBA i VBA innych klientów. W przypadku klientów spoza procesu dodatkowy kod jest konieczne, aby uniknąć sytuacji wyścigu możliwe.  
  
### <a name="access-objects-from-vba-solutions"></a>Uzyskiwanie dostępu do obiektów z rozwiązań VBA  
 Poniższy przykład kodu pokazuje, jak wywołać metodę, która jest uwidaczniany przez dodatku narzędzi VSTO za pomocą języka VBA. To makro VBA wywołuje metodę o nazwie `ImportData` zdefiniowanego w dodatku narzędzi VSTO dla programów, który nosi nazwę **ExcelImportData**. Aby wyświetlić ten kod w kontekście większych wskazówki, zobacz [instruktażu: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```vb
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="access-objects-from-non-vba-solutions"></a>Uzyskiwanie dostępu do obiektów z rozwiązania innego niż VBA  
 W ramach rozwiązania bez VBA należy rzutować wartość właściwości COMAddIn.Object interfejs, który implementuje, i wywoływać metody narażonych na obiekcie interfejsu. Poniższy przykład kodu pokazuje sposób wywołania `ImportData` metody z różnych dodatku narzędzi VSTO, który został utworzony przy użyciu narzędzi Office developer tools w programie Visual Studio.  
  
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
  
 W tym przykładzie, jeśli zostanie podjęta próba rzutować wartości właściwości COMAddIn.Object `AddInUtilities` klasy zamiast `IAddInUtilities` interfejsu, wygeneruje kod <xref:System.InvalidCastException>.  
  
## <a name="see-also"></a>Zobacz także  
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Przewodnik: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
