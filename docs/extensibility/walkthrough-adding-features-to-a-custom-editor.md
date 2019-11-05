---
title: 'Przewodnik: Dodawanie funkcji do edytora niestandardowego | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fa926b21171c3e09b5a0f4d74e9415da090bf2f
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2019
ms.locfileid: "73569073"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Przewodnik: Dodawanie funkcji do edytora niestandardowego
Po utworzeniu edytora niestandardowego można dodać do niego więcej funkcji.

## <a name="to-create-an-editor-for-a-vspackage"></a>Aby utworzyć Edytor dla elementu pakietu VSPackage

1. Utwórz niestandardowy Edytor przy użyciu szablonu projektu pakietu programu Visual Studio.

     Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego edytora](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Zdecyduj, czy edytor ma obsługiwać pojedynczy widok, czy wiele widoków.

     Edytor obsługujący nowe polecenie **okna** lub widok formularza i widok kodu wymaga oddzielnych obiektów danych dokumentu i obiektów widoku dokumentu. W edytorze, który obsługuje tylko jeden widok, obiekt danych dokumentu i obiekt widoku dokumentu można zaimplementować dla tego samego obiektu.

     Przykład wielu widoków można znaleźć w temacie [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md).

3. Zaimplementuj fabrykę edytora przez skonfigurowanie interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>.

     Aby uzyskać więcej informacji, zobacz [fabryki edytora](../extensibility/editor-factories.md).

4. Zdecyduj, czy edytor ma używać aktywacji w miejscu czy uproszczonego osadzania, aby zarządzać oknem obiektu widoku dokumentu.

     Uproszczone okno edytora osadzania zawiera standardowy widok dokumentu, podczas gdy okno edytora aktywacji w miejscu obsługuje formant ActiveX lub inny aktywny obiekt jako widok dokumentu. Aby uzyskać więcej informacji, zobacz [uproszczone osadzanie](../extensibility/simplified-embedding.md) i [Aktywacja w miejscu](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> w celu obsługi poleceń.

6. Podaj trwałość dokumentu i odpowiedź na zmiany plików zewnętrznych:

    1. Aby zachować plik, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> w obiekcie danych dokumentu edytora.

    2. Aby odpowiedzieć na zmiany w pliku zewnętrznym, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> w obiekcie danych dokumentu edytora.

        > [!NOTE]
        > Wywołaj `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>, aby uzyskać wskaźnik do `IVsFileChangeEx`.

7. Koordynuj zdarzenia edycji dokumentu z kontrolą kodu źródłowego. Wykonaj następujące kroki:

    1. Pobierz wskaźnik do `IVsQueryEditQuerySave2`, wywołując `QueryService` w <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.

    2. Gdy wystąpi pierwsze zdarzenie edycji, wywołaj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>.

         Ta metoda poprosi użytkownika o wyewidencjonowanie pliku, jeśli nie został jeszcze wyewidencjonowany. Pamiętaj, aby obsłużyć warunek "niewyewidencjonowany plik" w celu zapobieżenia błędom.

    3. Podobnie przed zapisaniem pliku Wywołaj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>.

         Ta metoda poprosi użytkownika o zapisanie pliku, jeśli nie został on zapisany lub zmieniono od ostatniego zapisu.

8. Włącz okno **Właściwości** , aby wyświetlić właściwości tekstu zaznaczonego w edytorze. Wykonaj następujące kroki:

    1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> za każdym razem, gdy zmienia się wybór tekstu, przekazując w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.

    2. Wywołaj `QueryService` w usłudze <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.

9. Zezwól użytkownikom na przeciąganie i upuszczanie elementów między edytorem i **przybornikiem**albo między edytorami zewnętrznymi (takimi jak program Microsoft Word) i **przybornikiem**. Wykonaj następujące kroki:

    1. Zaimplementuj `IDropTarget` w edytorze, aby ostrzec IDE, że edytorem jest obiekt docelowy upuszczania.

    2. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> w widoku, aby Edytor mógł włączać i wyłączać elementy w **przyborniku**.

    3. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> i Wywołaj `QueryService` w usłudze <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>, aby uzyskać wskaźnik do interfejsów <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>.

         Te kroki umożliwiają pakietu VSPackage Dodawanie nowych elementów do **przybornika**.

10. Zdecyduj, czy chcesz, aby wszystkie inne funkcje opcjonalne dla edytora.

    - Jeśli chcesz, aby Edytor obsługiwał polecenia Znajdź i Zamień, zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.

    - Jeśli chcesz użyć okna narzędzia konspektu dokumentu w edytorze, zaimplementuj `IVsDocOutlineProvider`.

    - Jeśli chcesz użyć paska stanu w edytorze, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> i Wywołaj `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>, aby uzyskać wskaźnik do `IVsStatusBar`.

         Na przykład, Edytor może wyświetlać informacje o wierszu/kolumnie, tryb wyboru (strumień/pole) i tryb wstawiania (Wstawianie/przekreślenie).

    - Jeśli chcesz, aby Edytor obsługiwał polecenie `Undo`, zalecana metoda to użycie modelu Menedżera obiektów OLE Undo. Alternatywnie, możesz mieć Edytor bezpośrednio obsłużyć `Undo` polecenie.

11. Utwórz informacje rejestru, w tym identyfikatory GUID dla pakietu VSPackage, menu, Edytor i inne funkcje.

     Poniżej przedstawiono ogólny przykład kodu, który można umieścić w skrypcie pliku *. RGS* , aby pokazać, jak prawidłowo zarejestrować Edytor.

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

     Ten krok pozwala udostępnić Pomoc F1 i dynamiczną obsługę okna pomocy dla elementów w edytorze. Aby uzyskać więcej informacji, zobacz [How to: zapewnianie kontekstu dla edytorów](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Uwidocznij model obiektów automatyzacji z edytora, implementując interfejs `IDispatch`.

     Aby uzyskać więcej informacji, zobacz temat Tworzenie [modelu automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Niezawodne programowanie

- Wystąpienie edytora jest tworzone, gdy IDE wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Jeśli Edytor obsługuje wiele widoków, `CreateEditorInstance` tworzy zarówno dane dokumentu, jak i obiekty widoku dokumentu. Jeśli obiekt danych dokumentu jest już otwarty, do `IVsEditorFactory::CreateEditorInstance`jest przenoszona wartość `punkDocDataExisting` o wartości innej niż null. Implementacja fabryki edytora musi określać, czy istniejący obiekt danych dokumentu jest zgodny przez wykonywanie zapytań dotyczących odpowiednich interfejsów. Aby uzyskać więcej informacji, zobacz [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md).

- Jeśli używasz uproszczonego podejścia do osadzania, zaimplementuj interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>.

- W przypadku podjęcia decyzji o użyciu aktywacji w miejscu należy zaimplementować następujące interfejsy:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Interfejs `IOleInPlaceComponent` jest używany, aby uniknąć scalania menu OLE 2.

   Implementacja `IOleCommandTarget` obsługuje polecenia, takie jak **wycinanie**, **Kopiowanie**i **wklejanie**. Podczas implementowania `IOleCommandTarget`Zdecyduj, czy Edytor wymaga własnego pliku *. vsct* , aby zdefiniować własną strukturę menu poleceń, czy też może zaimplementować standardowe polecenia zdefiniowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Zazwyczaj edytory używają i zwiększają menu środowiska IDE oraz definiują własne paski narzędzi. Niemniej jednak często konieczne jest, aby Edytor mógł definiować własne poszczególne polecenia oprócz używania standardowego zestawu poleceń IDE. Edytor musi deklarować standardowe polecenia, z których korzysta, a następnie definiować nowe polecenia, menu kontekstowe, menu najwyższego poziomu i paski narzędzi w pliku *. vsct* . Jeśli tworzysz Edytor aktywacji w miejscu, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> i zdefiniuj menu i paski narzędzi dla edytora w pliku *. vsct* , a nie za pomocą scalania menu OLE 2.

- Aby zapobiec zapisywaniu poleceń menu w interfejsie użytkownika, należy użyć istniejących poleceń w IDE przed wyjęciem nowych poleceń. Polecenia udostępnione są zdefiniowane w *SharedCmdDef. vsct* i *ShellCmdDef. vsct*. Te pliki są instalowane domyślnie w podkatalogu VisualStudioIntegration\Common\Inc instalacji [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].

- `ISelectionContainer` może wyrazić wybór pojedynczy i wielokrotny. Każdy wybrany obiekt jest implementowany jako obiekt `IDispatch`.

- IDE implementuje `IOleUndoManager` jako usługę dostępną z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> lub jako obiekt, który można utworzyć przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Edytor implementuje interfejs `IOleUndoUnit` dla każdej akcji `Undo`.

- Istnieją dwa miejsca, w których Edytor niestandardowy może uwidaczniać obiekty automatyzacji:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Zobacz także

- [Współtworzenie modelu automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md)