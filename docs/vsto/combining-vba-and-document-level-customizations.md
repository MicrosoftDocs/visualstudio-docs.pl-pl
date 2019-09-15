---
title: Łączenie języka VBA i dostosowań na poziomie dokumentu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b3bab9c132439c6efa53842f1e13c6c5be31db00
ms.sourcegitcommit: 6c55c40da74ed8969dcba56acbd30458fdb69c5a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70977604"
---
# <a name="combine-vba-and-document-level-customizations"></a>Łączenie języka VBA i dostosowań na poziomie dokumentu
  Możesz użyć kodu Visual Basic for Applications (VBA) w dokumencie, który jest częścią dostosowania na poziomie dokumentu dla Microsoft Office Word lub Microsoft Office Excel. Można wywołać kod języka VBA w dokumencie z zestawu dostosowania lub można skonfigurować projekt, aby umożliwić kod VBA w dokumencie, aby wywołać kod w zestawie dostosowywania.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Zachowanie kodu VBA w dostosowaniu na poziomie dokumentu
 Po otwarciu projektu w programie Visual Studio dokument zostanie otwarty w trybie projektowania. Kod VBA nie jest uruchamiany, gdy dokument jest w trybie projektowania, więc możesz pracować nad dokumentem i kodem bez uruchamiania kodu VBA.

 Po uruchomieniu rozwiązania programy obsługi zdarzeń w języku VBA i zestawie dostosowań pobierają zdarzenia, które zostały zgłoszone w dokumencie, oraz oba zestawy uruchamiania kodu. Przed drugim nie można określić, który kod zostanie uruchomiony. należy to określić za poorednictwem testowania w każdym indywidualnym przypadku. Możesz uzyskać nieoczekiwane wyniki, jeśli dwa zestawy kodu nie są starannie koordynowane i przetestowane.

## <a name="call-vba-code-from-the-customization-assembly"></a>Wywoływanie kodu VBA z zestawu dostosowania
 Możesz wywoływać makra w dokumentach programu Word i można wywoływać makra i funkcje w skoroszytach programu Excel. W tym celu należy użyć jednej z następujących metod:

- Dla programu Word Wywołaj <xref:Microsoft.Office.Interop.Word._Application.Run%2A> metodę <xref:Microsoft.Office.Interop.Word.Application> klasy.

- Dla programu Excel Zadzwoń <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> do metody <xref:Microsoft.Office.Interop.Excel.Application> klasy.

  Dla każdej metody pierwszy parametr określa nazwę makro lub funkcję, która ma zostać wywołana, a pozostałe parametry opcjonalne określają parametry do przekazania do makra lub funkcji. Pierwszy parametr może mieć różne formaty dla programów Word i Excel:

- Dla programu Word pierwszy parametr jest ciągiem, który może być dowolną kombinacją szablonu, modułu i nazwy makra. W przypadku określenia nazwy dokumentu, kod może uruchamiać tylko makra w dokumentach związanych z bieżącym kontekstem — nie tylko makro w żadnym dokumencie.

- W przypadku programu Excel pierwszy parametr może być ciągiem, który określa nazwę makra, <xref:Microsoft.Office.Interop.Excel.Range> która wskazuje, gdzie znajduje się funkcja, lub identyfikator rejestru dla zarejestrowanej funkcji DLL (XLL). W przypadku przekazania ciągu ciąg zostanie obliczony w kontekście aktywnego arkusza.

  Poniższy przykład kodu pokazuje, jak wywołać makro o nazwie `MyMacro` z projektu na poziomie dokumentu dla programu Excel. W tym przykładzie przyjęto założenie `Sheet1`, że `MyMacro` jest zdefiniowany w.

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Aby uzyskać informacje o używaniu `missing` zmiennej globalnej zamiast parametrów opcjonalnych w wizualizacji C#, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

## <a name="call-code-in-document-level-customizations-from-vba"></a>Wywoływanie kodu w dostosowaniach na poziomie dokumentu z języka VBA
 Można skonfigurować projekt na poziomie dokumentu dla programu Word lub Excel, aby kod Visual Basic for Applications (VBA) w dokumencie mógł wywołać kod w zestawie dostosowywania. Jest to przydatne w następujących scenariuszach:

- Chcesz rozłożyć istniejący kod języka VBA w dokumencie przy użyciu funkcji w dostosowaniu na poziomie dokumentu, które są skojarzone z tym samym dokumentem.

- Chcesz udostępnić usługi, które opracowujesz w dostosowaniu na poziomie dokumentu dostępnym dla użytkowników końcowych, którzy mogą uzyskiwać dostęp do usług, pisząc kod VBA w dokumencie.

  Narzędzia programistyczne pakietu Office w programie Visual Studio oferują podobną funkcję dla dodatków narzędzi VSTO. Jeśli tworzysz dodatek narzędzi VSTO, możesz wywołać kod w dodatku VSTO z innych rozwiązań Microsoft Office. Aby uzyskać więcej informacji, zobacz [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

> [!NOTE]
> Tej funkcji nie można używać w projektach szablonów programu Word. Może być używany tylko w projektach programu Word, skoroszytach programu Excel lub szablonach programu Excel.

## <a name="requirements"></a>Wymagania
 Przed włączeniem kodu VBA do wywołania zestawu dostosowania projekt musi spełniać następujące wymagania:

- Dokument musi mieć jedno z następujących rozszerzeń nazw plików:

  - Dla programu Word: *. docm* lub *. doc*

  - Dla programu Excel: *xlsm*, *. xltm*, *. xls*lub *. xlt*

- Dokument musi już zawierać projekt VBA, który zawiera kod VBA.

- Kod VBA w dokumencie musi być możliwy do uruchomienia bez monitowania użytkownika o włączenie makr. Można ufać kodzie VBA do uruchomienia przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word lub Excel.

- Projekt pakietu Office musi zawierać co najmniej jedną publiczną klasę, która zawiera co najmniej jednego członka publicznego, który jest ujawniany w języku VBA.

     Metody, właściwości i zdarzenia można uwidaczniać w języku VBA. Uwidaczniana Klasa może być klasą elementów hosta (na przykład `ThisDocument` dla programu Word `Sheet1` lub `ThisWorkbook` dla programu Excel) lub inną klasą zdefiniowaną w projekcie. Aby uzyskać więcej informacji na temat elementów hosta, zobacz [Omówienie elementów hosta i formantów hosta](../vsto/host-items-and-host-controls-overview.md).

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Włącz Wywoływanie kodu VBA z zestawem dostosowywania
 Istnieją dwa różne sposoby uwidaczniania elementów członkowskich w zestawie dostosowywania do kodu VBA w dokumencie:

- Można uwidocznić członków klasy elementu hosta w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projekcie w języku VBA. W tym celu należy ustawić właściwość **EnableVbaCallers** elementu hosta na **wartość true** w oknie **Właściwości** , podczas gdy element hosta (czyli dokument, arkusz lub skoroszyt) jest otwarty w projektancie. Program Visual Studio automatycznie wykonuje wszystkie czynności wymagane do włączenia kodu VBA do wywoływania elementów członkowskich klasy.

- Można uwidocznić składowe w dowolnej klasie publicznej w projekcie C# wizualnym lub członków w klasie elementów niebędących hostami w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projekcie w języku VBA. Ta opcja zapewnia większą swobodę w wyborze klas, które należy uwidocznić w języku VBA, ale wymaga również wykonania dodatkowych czynności ręcznych.

   W tym celu należy wykonać następujące główne czynności:

  1. Uwidocznij klasę w modelu COM.

  2. Zastąp metodę **GetAutomationObject** klasy elementu hosta w projekcie, aby zwrócić wystąpienie klasy, która jest uwidaczniana w języku VBA.

  3. Dla właściwości **ReferenceAssemblyFromVbaProject** każdej klasy elementów hosta w projekcie Ustaw **wartość true**. Spowoduje to osadzenie biblioteki typów zestawu dostosowania do zestawu i dodanie odwołania do biblioteki typów do projektu VBA w dokumencie.

  Aby uzyskać szczegółowe instrukcje, [zobacz How to: Uwidacznianie kodu w języku VBA w projekcie](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) Visual Basic [i instrukcje: Uwidacznianie kodu w języku VBA w projekcie&#35; ](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)Visual C.

  Właściwości **EnableVbaCallers** i **ReferenceAssemblyFromVbaProject** są dostępne tylko w oknie **Właściwości** w czasie projektowania. nie można ich używać w czasie wykonywania. Aby wyświetlić właściwości, Otwórz projektanta dla elementu hosta w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji na temat określonych zadań wykonywanych przez program Visual Studio podczas ustawiania tych właściwości, zobacz [zadania wykonywane przez właściwości elementu hosta](#PropertyTasks).

> [!NOTE]
> Jeśli skoroszyt lub dokument nie zawiera jeszcze kodu VBA lub jeśli kod VBA w dokumencie nie jest zaufany do uruchomienia, zostanie wyświetlony komunikat o błędzie po ustawieniu właściwości **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** na **wartość true**. Wynika to z faktu, że program Visual Studio nie może zmodyfikować projektu VBA w dokumencie w takiej sytuacji.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Użyj elementów członkowskich w kodzie języka VBA do wywołania zestawu dostosowania
 Po skonfigurowaniu projektu w celu włączenia kodu VBA do wywołania zestawu dostosowania program Visual Studio dodaje następujących członków do projektu VBA w dokumencie:

- W przypadku wszystkich projektów program Visual Studio dodaje metodę globalną `GetManagedClass`o nazwie.

- W [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] przypadku projektów, w których są ujawniane elementy członkowskie klasy elementu hosta za pomocą właściwości **EnableVbaCallers** , Visual `CallVSTOAssembly` Studio dodaje również `Sheet2` `ThisDocument`właściwość o nazwie, `ThisWorkbook`, `Sheet1`,, lub `Sheet3` moduł w projekcie VBA.

  Możesz użyć `CallVSTOAssembly` właściwości lub `GetManagedClass` metody, aby uzyskać dostęp do publicznych członków klasy, które zostały uwidocznione w kodzie VBA w projekcie.

> [!NOTE]
> Podczas opracowywania i wdrażania rozwiązania istnieje kilka różnych kopii dokumentu, w których można dodać kod języka VBA. Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące dodawania kodu VBA do dokumentu](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Używanie właściwości CallVSTOAssembly w projekcie Visual Basic
 `CallVSTOAssembly` Użyj właściwości, aby uzyskać dostęp do publicznych elementów członkowskich dodanych do klasy elementów hosta. Na przykład następujące makro języka VBA wywołuje metodę o nazwie `MyVSTOMethod` , która jest zdefiniowana `Sheet1` w klasie w projekcie skoroszytu programu Excel.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Ta właściwość jest bardziej wygodnym sposobem wywołania zestawu dostosowania niż bezpośrednio przy użyciu `GetManagedClass` metody. `CallVSTOAssembly`zwraca obiekt, który reprezentuje klasę elementu hosta, która została udostępniona do języka VBA. Parametry elementów członkowskich i metod zwracanego obiektu są wyświetlane w technologii IntelliSense.

 `CallVSTOAssembly` Właściwość ma deklarację podobną do poniższego kodu. W tym kodzie przyjęto założenie, `Sheet1` że Klasa elementu hosta została udostępniona w projekcie skoroszytu `ExcelWorkbook1` programu Excel o nazwie do VBA.

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>Użyj metody GetManagedClass
 Aby użyć metody globalnej `GetManagedClass` , należy przekazać obiekt języka VBA, który odpowiada klasie elementu hosta, która zawiera przesłonięcie metody **GetAutomationObject** . Następnie użyj zwróconego obiektu, aby uzyskać dostęp do klasy uwidocznionej w języku VBA.

 Na przykład następujące makro języka VBA wywołuje metodę o nazwie `MyVSTOMethod` , która jest zdefiniowana `Sheet1` w klasie elementów hosta w projekcie skoroszytu programu Excel o nazwie `ExcelWorkbook1`.

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 `GetManagedClass` Metoda ma następującą deklarację.

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Ta metoda zwraca obiekt, który reprezentuje klasę, która została udostępniona do języka VBA. Parametry elementów członkowskich i metod zwracanego obiektu są wyświetlane w technologii IntelliSense.

## <a name="Guidelines"></a>Wskazówki dotyczące dodawania kodu VBA do dokumentu
 Istnieje kilka różnych kopii dokumentu, w których można dodać kod języka VBA, który wywołuje dostosowanie na poziomie dokumentu.

 Podczas opracowywania i testowania rozwiązania można napisać kod języka VBA w dokumencie, który zostanie otwarty podczas debugowania lub uruchamiania projektu w programie Visual Studio (czyli dokumentu w folderze danych wyjściowych kompilacji). Jednak kod języka VBA dodany do tego dokumentu zostanie zastąpiony przy następnym skompilowaniu projektu, ponieważ program Visual Studio zastępuje dokument w folderze danych wyjściowych kompilacji kopią dokumentu z głównego folderu projektu.

 Jeśli chcesz zapisać kod języka VBA, który został dodany do dokumentu podczas debugowania lub uruchamiania rozwiązania, skopiuj kod VBA do dokumentu w folderze projektu. Aby uzyskać więcej informacji na temat procesu kompilacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

 Gdy wszystko będzie gotowe do wdrożenia rozwiązania, istnieją trzy lokalizacje dokumentów głównych, w których można dodać kod języka VBA.

### <a name="in-the-project-folder-on-the-development-computer"></a>W folderze projektu na komputerze deweloperskim
 Ta lokalizacja jest wygodna, jeśli masz pełną kontrolę nad kodem VBA w dokumencie i kodem dostosowania. Ponieważ dokument znajduje się na komputerze deweloperskim, można łatwo zmodyfikować kod języka VBA, jeśli zmienisz kod dostosowywania. Kod VBA dodany do tej kopii dokumentu pozostaje w dokumencie podczas kompilowania, debugowania i publikowania rozwiązania.

 Nie można dodać kodu VBA do dokumentu, gdy jest on otwarty w projektancie. Najpierw należy zamknąć dokument w projektancie, a następnie otworzyć go bezpośrednio w programie Word lub Excel.

> [!CAUTION]
> Jeśli dodasz kod języka VBA, który jest uruchamiany, gdy dokument zostanie otwarty, w rzadkich przypadkach ten kod może spowodować uszkodzenie dokumentu lub uniemożliwić jego otwarcie w projektancie.

### <a name="in-the-publish-or-installation-folder"></a>W folderze publikowania lub instalacji
 W niektórych przypadkach może być odpowiednie dodanie kodu VBA do dokumentu w folderze publikowania lub instalacji. Na przykład możesz wybrać tę opcję, jeśli kod VBA zostanie zapisany i przetestowany przez innego dewelopera na komputerze, na którym nie zainstalowano programu Visual Studio.

 Jeśli użytkownicy instalują rozwiązanie bezpośrednio z folderu publikowanie, należy dodać kod VBA do dokumentu przy każdym publikowaniu rozwiązania. Program Visual Studio zastąpi dokument w lokalizacji publikowania podczas publikowania rozwiązania.

 Jeśli użytkownicy instalują rozwiązanie z folderu instalacji innego niż folder publikacji, można uniknąć dodawania kodu VBA w dokumencie za każdym razem, gdy publikujesz rozwiązanie. Gdy aktualizacja publikowania jest gotowa do przeniesienia z folderu publikowania do folderu instalacji, skopiuj wszystkie pliki do folderu instalacji z wyjątkiem tego dokumentu.

### <a name="on-the-end-user-computer"></a>Na komputerze użytkownika końcowego
 Jeśli użytkownicy końcowi są programistami VBA, którzy dzwonią do usług, które zostały wprowadzone w dostosowaniu na poziomie dokumentu, można powiedzieć, jak wywoływać kod przy użyciu `CallVSTOAssembly` właściwości `GetManagedClass` lub metody w swoich kopiach dokumentu. Po opublikowaniu aktualizacji w rozwiązaniu kod języka VBA w dokumencie na komputerze użytkownika końcowego nie zostanie zastąpiony, ponieważ dokument nie jest modyfikowany przez aktualizacje publikacji.

## <a name="PropertyTasks"></a>Zadania wykonywane przez właściwości elementu hosta
 W przypadku używania właściwości **EnableVbaCallers** i **ReferenceAssemblyFromVbaProject** program Visual Studio wykonuje różne zestawy zadań.

### <a name="enablevbacallers"></a>EnableVbaCallers
 Po ustawieniu właściwości **EnableVbaCallers** elementu hosta na **wartość True** w projekcie Visual Basic program Visual Studio wykonuje następujące zadania:

1. Dodaje <xref:Microsoft.VisualBasic.ComClassAttribute> atrybuty i <xref:System.Runtime.InteropServices.ComVisibleAttribute> do klasy Item hosta.

2. Zastępuje metodę **GetAutomationObject** klasy elementu hosta.

3. Ustawia właściwość **ReferenceAssemblyFromVbaProject** elementu hosta na **wartość true**.

   Po ustawieniu właściwości **EnableVbaCallers** z powrotem na **wartość false**program Visual Studio wykonuje następujące zadania:

4. Usuwa <xref:Microsoft.VisualBasic.ComClassAttribute> atrybuty i <xref:System.Runtime.InteropServices.ComVisibleAttribute> z `ThisDocument` klasy.

5. Usuwa metodę **GetAutomationObject** z klasy Item hosta.

   > [!NOTE]
   > Program Visual Studio nie ustawia automatycznie właściwości **ReferenceAssemblyFromVbaProject** z powrotem na **wartość false**. Tę właściwość można ustawić na **wartość false** ręcznie przy użyciu okna **Właściwości** .

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Gdy właściwość **ReferenceAssemblyFromVbaProject** dowolnego elementu hosta w Visual Basic lub projekt wizualny C# ma **wartość true**, program Visual Studio wykonuje następujące zadania:

1. Generuje bibliotekę typów dla zestawu dostosowania i osadza bibliotekę typów w zestawie.

2. Dodaje odwołanie do następujących bibliotek typów w projekcie VBA w dokumencie:

   - Biblioteka typów dla zestawu dostosowania.

   - Biblioteka typów narzędzi Microsoft Visual Studio Tools dla aparatu wykonywania pakietu Office 9,0. Ta biblioteka typów jest uwzględniona w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

   Gdy właściwość **ReferenceAssemblyFromVbaProject** jest ustawiona na **wartość false**, program Visual Studio wykonuje następujące zadania:

3. Usuwa odwołania biblioteki typów z projektu VBA w dokumencie.

4. Usuwa osadzoną bibliotekę typów z zestawu.

## <a name="troubleshoot"></a>Rozwiązywanie problemów
 W poniższej tabeli wymieniono niektóre typowe błędy i sugestie dotyczące usuwania błędów.

|Błąd|Sugestia|
|-----------|----------------|
|Po ustawieniu właściwości **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** komunikat o błędzie stwierdza, że dokument nie zawiera projektu VBA lub nie masz uprawnień dostępu do projektu VBA w dokumencie.|Upewnij się, że dokument w projekcie zawiera co najmniej jedno makro VBA, projekt VBA ma wystarczające zaufanie do uruchomienia, a projekt VBA nie jest chroniony hasłem.|
|Po ustawieniu właściwości **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** komunikat o błędzie <xref:System.Runtime.InteropServices.GuidAttribute> stwierdza, że brakuje deklaracji lub jest ona uszkodzona.|Upewnij się, <xref:System.Runtime.InteropServices.GuidAttribute> że deklaracja znajduje się w pliku *AssemblyInfo.cs* lub *AssemblyInfo. vb* w projekcie, i że ten atrybut jest ustawiony na prawidłowy identyfikator GUID.|
|Po ustawieniu właściwości **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** komunikat o błędzie stwierdza, że numer wersji <xref:System.Reflection.AssemblyVersionAttribute> określony przez jest nieprawidłowy.|Upewnij się, <xref:System.Reflection.AssemblyVersionAttribute> że deklaracja w pliku *AssemblyInfo.cs* lub *AssemblyInfo. vb* w projekcie ma ustawiony prawidłowy numer wersji zestawu. Aby uzyskać informacje o prawidłowych numerach wersji zestawu <xref:System.Reflection.AssemblyVersionAttribute> , zobacz Klasa.|
|Po zmianie nazwy zestawu dostosowania kod języka VBA, który wywołuje do zestawu dostosowania, przestanie działać.|Jeśli zmienisz nazwę zestawu dostosowania po udostępnieniu go w kodzie VBA, link między projektem VBA w dokumencie a zestawem dostosowywania zostanie przerwany. Aby rozwiązać ten problem, Zmień właściwość **ReferenceFromVbaAssembly** w projekcie na **Fałsz** , a następnie z powrotem na **wartość true**, a następnie Zastąp wszystkie odwołania do starej nazwy zestawu w kodzie VBA z nową nazwą zestawu.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Uwidacznianie kodu w języku VBA w projekcie Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Instrukcje: Uwidacznianie kodu w języku VBA w projekcie&#35; Visual C](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Przewodnik: Wywoływanie kodu z VBA w projekcie Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Przewodnik: Wywoływanie kodu z VBA w projekcie Visual&#35; C](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Język VBA i rozwiązania pakietu Office w programie Visual Studio](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
