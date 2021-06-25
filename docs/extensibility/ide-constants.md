---
title: Stałe IDE | Microsoft Docs
description: Klasa VSConstants udostępnia stałe specyficzne dla środowiska IDE i wcześniej zdefiniowane tylko w plikach nagłówkowych.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
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
ms.openlocfilehash: 802de0fd29d909320040667f972de422595bdd4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904971"
---
# <a name="ide-constants"></a>Stałe IDE

Klasa zawiera stałe, które są specyficzne dla zintegrowanego środowiska projektowego (IDE), które zostały wcześniej zdefiniowane <xref:Microsoft.VisualStudio.VSConstants> tylko w plikach nagłówkowych.

## <a name="logical-and-physical-views"></a>Widoki logiczne i fizyczne

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Programy obsługi powinny przekazać tę wartość do metody , aby uzyskać okno dialogowe Otwórz za pomocą, w tym przypadku dotyczące `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> możliwych widoków kodu. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Programy obsługi przekażą tę wartość do metody w celu uzyskania okna dialogowego Otwórz za pomocą, w tym przypadku wypełnionych możliwymi widokami debugowania mapowanych na ten `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> sam widok co  <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Programy obsługi przekażą tę wartość do metody w celu uzyskania okna dialogowego Otwórz za pomocą, w tym `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> przypadku widoku **widoków projektanta** formularzy. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Programy obsługi przekażą tę wartość do metody w celu uzyskania okna dialogowego Otwórz za pomocą, w tym przypadku widoku `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> domyślnego/podstawowego fabryki edytora. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Programy obsługi przekażą tę wartość do metody w celu uzyskania okna dialogowego Otwórz za pomocą, w tym przypadku dla widoku edytora tekstów `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> dokumentów lub danych. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Programy obsługi przekażą tę wartość do metody , która monituje użytkownika o wybranie widoku `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> zdefiniowanego przez użytkownika do użycia.|

## <a name="editor-factory-flags"></a>Flagi fabryki edytora

|Wartość|Opis|
|-----------|-----------------|
|[Cef. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Przestarzała flaga łączyła bitowe wartości jako pierwszy parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody.|
|[Cef. OpenAsNw](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Połączone bitowo jako pierwszy parametr metody , co oznacza, że <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> fabryka edytorów powinna wykonać niezbędne poprawki.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Połączone bitowo jako pierwszy parametr metody, ta <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> flaga wzajemnie się wyklucza z [CEF. CloneFile .](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|
|[Cef. Cichy](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Połączone bitowo jako pierwszy parametr metody, oznacza to, że fabryka edytora powinna utworzyć edytor bez <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> wyświetlania interfejsu użytkownika.|

## <a name="visual-studio-errors"></a>Visual Studio błędów

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Stała zwracana przez interfejsy do zachowania asynchronicznego, gdy obiekt, który jest już zajęty|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Błąd HRESULT specyficzny dla Visual Studio dla "niezgodnych danych dokumentu".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Błąd HRESULT, który jest specyficzny dla Visual Studio i który wskazuje "Pakiet nie został załadowany".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Błąd HRESULT specyficzny dla Visual Studio, który wskazuje, że "Projekt już istnieje".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Błąd HRESULT, który jest specyficzny dla Visual Studio i który wskazuje "Konfiguracja projektu nie powiodła się".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Błąd HRESULT, który jest specyficzny dla Visual Studio i który wskazuje "Projekt nie został załadowany".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Błąd HRESULT, który jest specyficzny dla Visual Studio i który wskazuje "Rozwiązanie jest już otwarte".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Błąd HRESULT, który jest specyficzny dla Visual Studio i który wskazuje "Rozwiązanie nie jest otwarte".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Zwracane przez interfejsy kompilacji, które mają parametry służące do określania tablicy z interfejsu, ale implementacja może zastosować <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> metodę tylko do wszystkich danych wyjściowych.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Metoda <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> zwraca tę wartość, jeśli dokument ma format, który nie może zostać otwarty w edytorze.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Wartość HRESULT, która wskazuje, że użytkownik nacisnie przycisk Wstecz w kreatorze Visual Studio danych.|

## <a name="visual-studio-constants"></a>Visual Studio stałe

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Błąd HRESULT, który jest specyficzny dla Visual Studio i który wskazuje "Project forwarded".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Stała specyficzna dla Visual Studio "Znacznik przybornika".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Stała specyficzna dla Visual Studio do emitowania komunikatu powiadomienia za pośrednictwem metody , która wskazuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> początek niechęci.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Stała specyficzna dla Visual Studio do emitowania komunikatu powiadomienia za pośrednictwem metody , która wskazuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> koniec nieswoich.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Stała specyficzna dla Visual Studio do rozgłaszenia komunikatu powiadomienia za pośrednictwem metody wskazującej, że metryki paska <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> poleceń uległy zmianie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Stała specyficzna dla Visual Studio, która wskazuje, że plik cookie nie został ustawiony.|
|[VSITEMID. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identyfikator Visual Studio, który reprezentuje brak elementu projektu. Ta wartość jest używana, gdy nie ma bieżącego wyboru.|
|[VSITEMID. Głównego](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identyfikator Visual Studio, który reprezentuje katalog główny hierarchii projektu i służy do identyfikowania całej hierarchii, w przeciwieństwie do pojedynczego elementu.|
|[VSITEMID. Wybór](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identyfikator Visual Studio reprezentujący aktualnie wybrany element lub elementy, które mogą zawierać katalog główny hierarchii.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Opisuje, który składnik środowiska IDE został właśnie wybrany, na przykład w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> wywołaniu .

|Stała|Wartość|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Stałe używane do wskazywania nowego stanu wyboru.

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

- [Polecenia zdefiniowane w ideu do rozszerzania systemów projektów](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
