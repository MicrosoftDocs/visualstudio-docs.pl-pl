---
title: Stałe IDE | Microsoft Docs
description: Klasa VSConstants zapewnia stałe specyficzne dla środowiska IDE i, które zostały wcześniej zdefiniowane tylko w plikach nagłówkowych.
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66daa52bc5769a9f8b599a52953a6bc898d2cf20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069871"
---
# <a name="ide-constants"></a>Stałe IDE

<xref:Microsoft.VisualStudio.VSConstants>Klasa zawiera stałe, które są specyficzne dla zintegrowanego środowiska programistycznego (IDE) i które zostały wcześniej zdefiniowane tylko w plikach nagłówkowych.

## <a name="logical-and-physical-views"></a>Widoki logiczne i fizyczne

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`procedury obsługi powinny przekazać tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody w celu uzyskania okna dialogowego **Otwórz za pomocą** , w tym przypadku w możliwych widokach kodu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`procedury obsługi przekazują tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody w celu uzyskania okna dialogowego **Otwórz za pomocą** , w tym przypadku wypełniania możliwymi <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> widokami debugowania, które mapują do tego samego widoku co <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`procedury obsługi przekazują tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody w celu uzyskania okna dialogowego **Otwórz za pomocą** , w tym przypadku do wyświetlania widoków projektanta **formularzy** .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`procedury obsługi przekazują tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody w celu uzyskania okna dialogowego **Otwórz za pomocą** , w tym przypadku widoku domyślnego/podstawowego fabryki edytora.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`procedury obsługi przekazują tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody w celu uzyskania okna dialogowego **Otwórz za pomocą** w tym przypadku widoku edytora tekstu dokumentu lub danych.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`procedury obsługi przekazują tę wartość do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody, która wyświetla użytkownikowi komunikat, aby wybrać widok zdefiniowany przez użytkownika, który ma być używany.|

## <a name="editor-factory-flags"></a>Flagi fabryki edytora

|Wartość|Opis|
|-----------|-----------------|
|[CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Przestarzała flaga połączone jako pierwszy parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody.|
|[CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Połączone bitowe jako pierwszy parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, oznacza to, że fabryka edytorów powinna wykonać niezbędne poprawki.|
|[CEF. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Połączone bitowe jako pierwszy parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, ta flaga wzajemnie się wykluczają z [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. Automatycznie](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Połączone bitowe jako pierwszy parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, oznacza to, że fabryka edytora powinien utworzyć Edytor bez wyświetlania interfejsu użytkownika.|

## <a name="visual-studio-errors"></a>Błędy programu Visual Studio

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Stała zwrócona przez interfejsy na zachowanie asynchroniczne, gdy obiekt w danym momencie jest już zajęty|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio dla "niezgodne dane dokumentu".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje "pakiet nie został załadowany".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i wskazuje, że "projekt już istnieje".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i wskazuje, że konfiguracja projektu nie powiodła się.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i wskazuje "projekt nie został załadowany".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i wskazuje, że rozwiązanie jest już otwarte.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i wskazuje "rozwiązanie nie jest otwarte".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Zwracane przez interfejsy kompilacji, które mają parametry do określania tablicy z <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interfejsu, ale implementacja może stosować metodę tylko do wszystkich danych wyjściowych.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>Metoda zwraca tę wartość, jeśli dokument ma format, którego nie można otworzyć w edytorze.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Wartość HRESULT wskazująca, że użytkownik uderzy przycisk Wstecz w Kreatorze programu Visual Studio.|

## <a name="visual-studio-constants"></a>Stałe programu Visual Studio

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje "przesłanie dalej projektu".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Stała, która jest specyficzna dla programu Visual Studio dla "znacznika przybornika".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Stała, która jest specyficzna dla programu Visual Studio do rozgłaszania komunikatu powiadomienia za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metody, która wskazuje początek modalności.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Stała, która jest specyficzna dla programu Visual Studio do rozgłaszania komunikatu powiadomienia za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metody wskazującej koniec modalności.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Stała, która jest specyficzna dla programu Visual Studio do rozgłaszania komunikatu powiadomienia za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metody wskazującej, że metryki paska poleceń zostały zmienione.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Stała określona dla programu Visual Studio, która wskazuje, że plik cookie nie został ustawiony.|
|[VSITEMID. Bezcłowy](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identyfikator elementu programu Visual Studio, który reprezentuje nieobecność elementu projektu. Ta wartość jest używana, gdy nie ma bieżącego wyboru.|
|[VSITEMID. Pierwiastek](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identyfikator elementu programu Visual Studio reprezentujący element główny hierarchii projektu i służy do identyfikowania całej hierarchii, w przeciwieństwie do pojedynczego elementu.|
|[VSITEMID. Wybór](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identyfikator elementu programu Visual Studio reprezentujący aktualnie wybrany element lub elementy, które mogą zawierać katalog główny hierarchii.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Opisuje, jaki składnik IDE został właśnie wybrany, w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> wywołaniu, na przykład.

|Stała|Wartość|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[Selectionelement. PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[Selectionelement. StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[Wybórelement. UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[Selectionelement. UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[Selectionelement. WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Stałe używane do wskazywania nowego stanu zaznaczenia.

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

## <a name="component-selector-dialog-constants"></a>Stałe okna dialogowego selektora składników

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

## <a name="see-also"></a>Zobacz też

- [Polecenia zdefiniowane w środowisku IDE służące do rozszerzania systemów projektów](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
