---
title: Stałe środowiska IDE | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbe90c182ada4d7e69313ff570b2f7d26087170c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929561"
---
# <a name="ide-constants"></a>Stałe środowiska IDE

<xref:Microsoft.VisualStudio.VSConstants> Klasa zawiera stałe, które dotyczą zintegrowanego środowiska programistycznego (IDE) i które zostały wcześniej zdefiniowane tylko w plikach nagłówkowych.

## <a name="logical-and-physical-views"></a>Widoki logiczne i fizyczne

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi, powinna przekazać tę wartość, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby uzyskać **Otwórz za pomocą** okno dialogowe, w tym przypadku dla widoków możliwych kodu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazuje tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby uzyskać **Otwórz za pomocą** okno dialogowe, w tym przypadku są wypełniane przy użyciu możliwości <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> debugowania widoków, które mapują do tego samego widoku <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazuje tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby uzyskać **Otwórz za pomocą** okno dialogowe, w tym przypadku celem **Wyświetl formularz** projektanta widoków.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazuje tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby uzyskać **Otwórz za pomocą** okno dialogowe, w tym przypadku widok domyślny/podstawowej fabryki edytora.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazuje tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby uzyskać **Otwórz za pomocą** okno dialogowe, w tym dla dokumentu lub dane widoku edytora tekstu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazuje tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody, który monituje użytkownika o wybranie widoku zdefiniowane przez użytkownika do użycia.|

## <a name="editor-factory-flags"></a>Flagi fabryki edytora

|Wartość|Opis|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Przestarzałe flagi bitowe jako pierwszy parametr w połączeniu <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody.|
|[CEF.OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Bitowe or jako pierwszy parametr w połączeniu <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, metody, oznacza to, fabryki edytora, należy wykonać niezbędnych poprawek.|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Bitowe or jako pierwszy parametr w połączeniu <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, ta flaga jest wzajemnie exclusive [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Bitowe or jako pierwszy parametr w połączeniu <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, oznacza to, fabryki edytora należy utworzyć edytora bez wyświetlania interfejsu użytkownika (UI).|

## <a name="visual-studio-errors"></a>Visual Studio errors

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Stała zwracana przez interfejsy zachowanie asynchroniczne po danego obiektu w już zajęty|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Błąd HRESULT, które są specyficzne dla programu Visual Studio "niezgodne dokument danych".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Błąd HRESULT, które są specyficzne dla programu Visual Studio i że wskazuje "Pakiet nie został załadowany."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Błąd HRESULT, które są specyficzne dla programu Visual Studio i że wskazuje, że "Projektu już istnieje".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Błąd HRESULT, które są specyficzne dla programu Visual Studio i że wskazuje "Konfiguracja projektu nie powiodło się."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Błąd HRESULT, które są specyficzne dla programu Visual Studio i że wskazuje "Nie załadowano projektu".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Błąd HRESULT, które są specyficzne dla programu Visual Studio i że wskazuje "Rozwiązanie już otwarty."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Błąd HRESULT, które są specyficzne dla programu Visual Studio i że wskazuje "Rozwiązania nie otwarte."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Zwrócone przez interfejsy kompilacji, które mają parametry w celu określenia tablicę z <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interfejsu, lecz implementacja może dotyczyć tylko metody wszystkie dane wyjściowe.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Metoda zwraca tę wartość, jeśli dokument ma format, którego nie można otworzyć w edytorze.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Wartość HRESULT, która wskazuje, że użytkownik, kliknij przycisk Wstecz w Kreatorze programu Visual Studio.|

## <a name="visual-studio-constants"></a>Visual Studio — stałe

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Błąd HRESULT, które są specyficzne dla programu Visual Studio i że wskazuje "Przekazywane projektu".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Stała, które są specyficzne dla programu Visual Studio "znacznika przybornika".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Stała, które są specyficzne dla programu Visual Studio do emitowania komunikatu powiadomienia za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodę, która wskazuje początek modalności.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Stała, które są specyficzne dla programu Visual Studio do emitowania komunikatu powiadomienia za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodę, która wskazuje koniec modalności.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Stała, które są specyficzne dla programu Visual Studio do emitowania komunikatu powiadomienia za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metoda wskazujący, że metryki paska poleceń zostały zmienione.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Stała, które są specyficzne dla programu Visual Studio, która wskazuje, czy plik cookie nie została ustawiona.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identyfikator elementu programu Visual Studio, który reprezentuje braku elementu projektu. Ta wartość jest używana, gdy nie ma bieżącego zaznaczenia.|
|[VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identyfikator elementu programu Visual Studio, który reprezentuje katalog główny hierarchii projektu i jest używany do identyfikowania całej hierarchii, w przeciwieństwie do pojedynczego elementu.|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identyfikator elementu programu Visual Studio, który reprezentuje aktualnie wybranego elementu lub elementów, które mogą zawierać elementu głównego hierarchii.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 W tym artykule opisano, jakie części IDE właśnie zostało zaznaczone, w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> na przykład wywoływać.

|Stała|Wartość|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Stałe używane do wskazania nowy stan zaznaczenia.

|Stała|Wartość|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Stałe okna dialogowego selektora składnika

|Stała|Wartość|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Zobacz także

- [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)