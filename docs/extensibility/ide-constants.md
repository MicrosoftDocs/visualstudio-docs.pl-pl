---
title: Stałe IDE | Dokumenty firmy Microsoft
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710502"
---
# <a name="ide-constants"></a>Stałe IDE

Klasa <xref:Microsoft.VisualStudio.VSConstants> zapewnia stałe, które są specyficzne dla zintegrowanego środowiska programistycznego (IDE) i które zostały wcześniej zdefiniowane tylko w plikach nagłówkowych.

## <a name="logical-and-physical-views"></a>Widoki logiczne i fizyczne

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` programy obsługi powinny przekazać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> tę wartość do metody, aby uzyskać okno dialogowe **Otwórz z,** w tym przypadku w możliwych widoków kodu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` programy obsługi przekazują <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> tę wartość do metody, aby uzyskać okno dialogowe **Otwórz za** pomocą, w tym przypadku wypełnione możliwymi <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> widokami debugowania, które są mapowane do tego samego widoku co <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` programy obsługi przekazać tę <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> wartość do metody, aby uzyskać okno dialogowe **Otwórz z,** w tym przypadku do **widoku widoków projektanta formularza.**|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` programy obsługi przekazują <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> tę wartość do metody, aby uzyskać okno dialogowe **Otwórz za pomocą,** w tym przypadku domyślny/podstawowy widok fabryki edytora.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` programy obsługi przekazują <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> tę wartość do metody, aby uzyskać okno dialogowe **Otwórz za** pomocą, w tym dla widoku edytora tekstu dokumentu lub danych.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` programy obsługi przekazać tę <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> wartość do metody, która monituje użytkownika, aby wybrać widok zdefiniowany przez użytkownika do użycia.|

## <a name="editor-factory-flags"></a>Flagi fabryczne edytora

|Wartość|Opis|
|-----------|-----------------|
|[Cef. Plik CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Przestarzała flaga połączona bitowo <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> jako pierwszy parametr metody.|
|[Cef. OpenAsNowy](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Połączone bitowe jako pierwszy <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>parametr metody , oznacza to, że fabryka edytora powinna wykonać niezbędne poprawki.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Połączone bitowe jako pierwszy <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> parametr metody, ta flaga jest wzajemnie wyklucza [cef. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Cichy](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Połączone bitowe jako pierwszy <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> parametr metody, oznacza to, że fabryka edytora należy utworzyć edytor bez wyświetlania interfejsu użytkownika (UI).|

## <a name="visual-studio-errors"></a>Błędy programu Visual Studio

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Stała zwracana przez interfejsy do zachowania asynchroniowego, gdy dany obiekt jest już zajęty|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio dla "Niezgodne dane dokumentu".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje "Pakiet nie jest załadowany."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje, że "Projekt już istnieje".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje "Konfiguracja projektu nie powiodła się".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje "Projekt nie załadowany."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje "Rozwiązanie już otwarte."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje "Rozwiązanie nie jest otwarte."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Zwracany przez interfejsy kompilacji, które mają <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> parametry do określania tablicy z interfejsu, ale implementacja może zastosować metodę tylko do wszystkich wyjść.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Metoda <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> zwraca tę wartość, jeśli dokument ma format, który nie może być otwarty w edytorze.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Wartość HRESULT, która wskazuje, że użytkownik nacisnąć przycisk wstecz w kreatorze programu Visual Studio.|

## <a name="visual-studio-constants"></a>Stałe programu Visual Studio

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Błąd HRESULT, który jest specyficzny dla programu Visual Studio i który wskazuje "Projekt przekazywane dalej."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Stała, która jest specyficzna dla programu Visual Studio dla "Toolbox markera".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Stała, która jest specyficzna dla programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Visual Studio do emitowania komunikatu powiadomień za pomocą metody, która wskazuje początek modalności.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Stała, która jest specyficzna dla programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Visual Studio do emitowania komunikatu powiadomień za pomocą metody, która wskazuje koniec modalności.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Stała, która jest specyficzna dla programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Visual Studio do emitowania komunikatu powiadomień za pomocą metody wskazującej, że metryki paska poleceń uległy zmianie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Stała, która jest specyficzna dla programu Visual Studio, która wskazuje, że plik cookie nie został ustawiony.|
|[VSITEMID. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identyfikator elementu programu Visual Studio, który reprezentuje brak elementu projektu. Ta wartość jest używana, gdy nie ma bieżącego wyboru.|
|[VSITEMID. Głównego](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identyfikator elementu programu Visual Studio, który reprezentuje katalog główny hierarchii projektu i jest używany do identyfikowania całej hierarchii, w przeciwieństwie do pojedynczego elementu.|
|[VSITEMID. Wybór](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identyfikator elementu programu Visual Studio reprezentujący aktualnie wybrany element lub elementy, które mogą zawierać katalog główny hierarchii.|

## <a name="ivsselectionevents"></a>IVsWyboryWydacje
 Opisuje, jaki składnik IDE właśnie został <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> wybrany, na przykład w wywołaniu.

|Stały|Wartość|
|--------------|-----------|
|[Ramka selectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[Identyfikator SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.Cofnij menedżer](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID ( VSSELELEMID )
 Stałe używane do wskazywania nowego stanu zaznaczenia.

|Stały|Wartość|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Stałe okna dialogowe selektora komponentów

|Stały|Wartość|
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

- [Polecenia zdefiniowane przez IDE do rozszerzania systemów projektowych](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
