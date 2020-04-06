---
title: 'Przewodnik: Dodawanie funkcji do edytora niestandardowego | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b145dd4d82887122009553afd883abb6cade849e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697788"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Przewodnik: Dodawanie funkcji do edytora niestandardowego
Po utworzeniu edytora niestandardowego można dodać do niego więcej funkcji.

## <a name="to-create-an-editor-for-a-vspackage"></a>Aby utworzyć edytor dla vspackage

1. Utwórz edytor niestandardowy przy użyciu szablonu projektu pakietu programu Visual Studio.

     Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie edytora niestandardowego](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Zdecyduj, czy edytor ma obsługiwać pojedynczy widok, czy wiele widoków.

     Edytor obsługujący polecenie **Nowe okno** lub zawierający widok formularza i widok kodu wymaga oddzielnych obiektów danych dokumentu i obiektów widoku dokumentu. W edytorze obsługującym tylko jeden widok obiekt danych dokumentu i obiekt widoku dokumentu mogą być implementowane na tym samym obiekcie.

     Aby zapoznać się z przykładem wielu widoków, zobacz [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).

3. Zaimplementuj fabrykę edytora, konfigurując <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejs.

     Aby uzyskać więcej informacji, zobacz [Fabryki edytorów](../extensibility/editor-factories.md).

4. Zdecyduj, czy edytor ma używać aktywacji w miejscu, czy uproszczonego osadzania do zarządzania oknem obiektu widoku dokumentu.

     Uproszczone okno edytora osadzania obsługuje standardowy widok dokumentu, podczas gdy okno edytora aktywacji w miejscu obsługuje formant ActiveX lub inny aktywny obiekt jako widok dokumentu. Aby uzyskać więcej informacji, zobacz [Uproszczone osadzanie](../extensibility/simplified-embedding.md) i [aktywacja w miejscu](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs do obsługi poleceń.

6. Zapewnij trwałość dokumentu i odpowiedź na zewnętrzne zmiany plików:

    1. Aby utrwalić <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> plik, zaimplementuj i na obiekcie danych dokumentu edytora.

    2. Aby reagować na zewnętrzne <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> zmiany plików, zaimplementuj i na obiekcie danych dokumentu edytora.

        > [!NOTE]
        > Zadzwoń, `QueryService` aby uzyskać `IVsFileChangeEx`wskaźnik do . <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>

7. Współrzęduj zdarzenia edycji dokumentu za pomocą kontroli kodu źródłowego. Wykonaj następujące kroki:

    1. Pobierz wskaźnik, `IVsQueryEditQuerySave2` wywołując `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>przycisk .

    2. Po wystąpieniu pierwszego zdarzenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> edycji wywołaj metodę.

         Ta metoda monituje użytkownika o wyewidencjonowanie pliku, jeśli nie jest on jeszcze wyewidencjonowany. Pamiętaj, aby obsłużyć warunek "plik nie wyewidencjonowany", aby uniknąć błędów.

    3. Podobnie przed zapisaniem pliku, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> wywołać metodę.

         Ta metoda monituje użytkownika o zapisanie pliku, jeśli nie został zapisany lub został zmieniony od czasu ostatniego zapisu.

8. Włącz okno **Właściwości,** aby wyświetlić właściwości tekstu zaznaczonego w edytorze. Wykonaj następujące kroki:

    1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> za każdym razem, gdy <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>zmienia się wybór tekstu, przechodząc w implementacji .

    2. Zadzwoń `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> do serwisu, aby <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>uzyskać wskaźnik do .

9. Umożliwianie użytkownikom przeciągania i upuszczania elementów między edytorem a **przybornikem**lub między zewnętrznymi edytorami (takimi jak Microsoft Word) a **przybornikami**. Wykonaj następujące kroki:

    1. Zaimplementuj `IDropTarget` w edytorze, aby ostrzec IDE, że edytor jest celem upuszczania.

    2. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfejs w widoku, aby edytor mógł włączać i wyłączać elementy w **przyborniku**.

    3. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> i `QueryService` wywołaj usługę, <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfejsów.

         Te kroki umożliwiają vspackage, aby dodać nowe elementy do **przybornika**.

10. Zdecyduj, czy chcesz mieć inne funkcje opcjonalne dla edytora.

    - Jeśli chcesz, aby edytor obsługiwał polecenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>znajdowania i zamieniania, zaimplementuj .

    - Jeśli chcesz użyć okna narzędzia konspektu `IVsDocOutlineProvider`dokumentu w edytorze, zaimplementuj program .

    - Jeśli chcesz użyć paska stanu w <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> edytorze, zaimplementuj i zadzwoń, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> aby uzyskać wskaźnik do `IVsStatusBar`.

         Na przykład edytor może wyświetlać informacje o wierszu / kolumnie, tryb wyboru (strumień / pudełko) i tryb wstawiania (wstawianie / przeciążenie).

    - Jeśli chcesz, aby edytor `Undo` obsługiwał polecenie, zalecaną metodą jest użycie modelu menedżera ole cofania. Alternatywnie, można mieć edytor obsługi `Undo` polecenia bezpośrednio.

11. Utwórz informacje rejestru, w tym identyfikatory GUID dla VSPackage, menu, edytor i inne funkcje.

     Poniżej przedstawiono ogólny przykład kodu, który można umieścić w skrypcie pliku *.rgs,* aby zademonstrować, jak prawidłowo zarejestrować edytora.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. Zaimplementuj obsługę pomocy kontekstowej.

     Ten krok umożliwia zapewnienie obsługi okien Pomocy F1 i dynamicznej pomocy dla elementów w edytorze. Aby uzyskać więcej informacji, zobacz [Jak: Podaj kontekst dla edytorów](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Uwidaczniać model obiektu automatyzacji `IDispatch` z edytora, implementując interfejs.

     Aby uzyskać więcej informacji, zobacz [Współtworzenie modelu automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Solidne programowanie

- Wystąpienie edytora jest tworzony, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> gdy IDE wywołuje metodę. Jeśli edytor obsługuje wiele `CreateEditorInstance` widoków, tworzy zarówno dane dokumentu, jak i obiekty widoku dokumentu. Jeśli obiekt danych dokumentu jest już otwarty, wartość nienawiązka jest `punkDocDataExisting` przekazywana do `IVsEditorFactory::CreateEditorInstance`. Implementacja fabryki edytora musi określić, czy istniejący obiekt danych dokumentu jest zgodny przez zapytanie o odpowiednie interfejsy na nim. Aby uzyskać więcej informacji, zobacz [Obsługa wielu widoków dokumentów](../extensibility/supporting-multiple-document-views.md).

- Jeśli używasz uproszczonego podejścia osadzania, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejs.

- Jeśli zdecydujesz się użyć aktywacji w miejscu, należy zaimplementować następujące interfejsy:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Interfejs `IOleInPlaceComponent` służy do uniknięcia scalania menu OLE 2.

   Implementacja `IOleCommandTarget` obsługuje polecenia, takie jak **Wytnij,** **Kopiuj**i **Wklej**. Podczas implementowania `IOleCommandTarget`zdecyduj, czy edytor wymaga własnego pliku *vsct* do zdefiniowania własnej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]struktury menu poleceń, czy też może implementować standardowe polecenia zdefiniowane przez program . Zazwyczaj edytory używają i rozszerzają menu IDE i definiują własne paski narzędzi. Jednak często jest to konieczne dla edytora, aby zdefiniować własne polecenia specyficzne oprócz korzystania ze standardowego zestawu poleceń IDE. Edytor musi zadeklarować standardowe polecenia, których używa, a następnie zdefiniować wszystkie nowe polecenia, menu kontekstowe, menu najwyższego poziomu i paski narzędzi w pliku *vsct.* Jeśli utworzysz edytor aktywacji <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> w miejscu, zaimplementuj i zdefiniuj menu i paski narzędzi dla edytora w pliku *vsct* zamiast scalania menu OLE 2.

- Aby zapobiec zatłoczenie polecenia menu w interfejsie użytkownika, należy użyć istniejących poleceń w IDE przed wynalezieniem nowych poleceń. Polecenia udostępnione są definiowane w *pliku SharedCmdDef.vsct* i *ShellCmdDef.vsct*. Pliki te są instalowane domyślnie w podkatalogu [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VisualStudioIntegration\Common\Inc instalacji.

- `ISelectionContainer`może wyrażać zarówno pojedyncze, jak i wielokrotne selekcje. Każdy zaznaczony obiekt jest `IDispatch` implementowany jako obiekt.

- IDE implementuje `IOleUndoManager` jako usługę dostępną <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> z lub jako obiekt, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>który można utworzyć wystąpienia za pośrednictwem . Edytor implementuje `IOleUndoUnit` interfejs dla `Undo` każdej akcji.

- Istnieją dwa miejsca, w których edytor niestandardowy może udostępniać obiekty automatyzacji:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Zobacz też

- [Współtworzenie modelu automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md)
