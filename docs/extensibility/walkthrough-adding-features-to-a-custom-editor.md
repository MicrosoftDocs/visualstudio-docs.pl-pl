---
title: 'Przewodnik: Dodawanie funkcji do edytora niestandardowego | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: afbde92cd666e0e67b1e70b0b4899c09d8b5b3e7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411072"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Przewodnik: Dodawanie funkcji do edytora niestandardowego
Po utworzeniu niestandardowego edytora, możesz dodać więcej funkcji do niego.

## <a name="to-create-an-editor-for-a-vspackage"></a>Aby utworzyć edytora dla pakietu VSPackage

1. Tworzenie niestandardowego edytora za pomocą szablonu projektu pakietu Visual Studio.

     Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie niestandardowego edytora](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Zdecyduj, czy chcesz tego edytora, aby obsługiwać pojedynczy widok lub wielu widoków.

     Edytor który obsługuje **nowe okno** polecenia lub widok formularza i widoku kodu, wymaga obiekty danych oddzielny dokument i Widok dokumentu. W edytorze, który obsługuje tylko jeden widok można zaimplementować obiekt danych dokumentu i obiekt widoku dokumentu na tym samym obiekcie.

     Na przykład wiele widoków, zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).

3. Implementowanie fabryki edytora, konfigurując <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu.

     Aby uzyskać więcej informacji, zobacz [fabryki edytora](../extensibility/editor-factories.md).

4. Zdecydować, czy mają tego edytora, aby korzystać z aktywacji w miejscu, czy uproszczone osadzanie Zarządzanie okna dokumentu widok obiektu.

     Uproszczone osadzanie okno edytora hostuje widokiem żadnego standardowego dokumentu, gdy okno edytora aktywacji w miejscu obsługuje formant ActiveX lub innego aktywnego obiektu jako jego widok dokumentu. Aby uzyskać więcej informacji, zobacz [uproszczone osadzanie](../extensibility/simplified-embedding.md) i [Aktywacja w miejscu](../extensibility/in-place-activation.md).

5. Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu do obsługi poleceń.

6. Podaj trwałość dokumentu i odpowiedzi na zmiany plików zewnętrznych:

    1. Aby utrwalić pliku, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> na obiekt danych dokumentu w edytorze.

    2. Aby reagować na zmiany pliku zewnętrznego, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> na obiekt danych dokumentu w edytorze.

        > [!NOTE]
        > Wywołaj `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> uzyskać wskaźnik do `IVsFileChangeEx`.

7. Koordynowanie zdarzeń edycji dokumentów kontroli kodu źródłowego. Wykonaj następujące kroki:

    1. Pobierz wskaźnik do `IVsQueryEditQuerySave2` przez wywołanie metody `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.

    2. Gdy wystąpi pierwsze zdarzenie edycji, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody.

         Ta metoda monituje użytkownika o wyewidencjonować pliku, jeśli jeszcze nie został wyewidencjonowany. Pamiętaj obsłużyć warunek "nie wyewidencjonować pliku" w celu uniknięcia błędów.

    3. Podobnie, przed zapisaniem pliku, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> metody.

         Ta metoda monituje użytkownika o zapisanie pliku, jeśli nie został zapisany lub jego zmienione od ostatniego zapisu.

8. Włącz **właściwości** okno, aby wyświetlić właściwości zaznaczonego w edytorze tekstu. Wykonaj następujące kroki:

    1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> każdego zaznaczonego tekstu czasu zmiany zakończone powodzeniem w danej implementacji <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.

    2. Wywołaj `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> usługę, aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.

9. Umożliwianie użytkownikom przeciągać i upuszczać elementy między edytora i **przybornika**, lub między edytory zewnętrzne (na przykład program Microsoft Word) i **przybornika**. Wykonaj następujące kroki:

    1. Implementowanie `IDropTarget` w edytorze do wyzwalania alertu IDE, że edytora jest miejsca docelowego.

    2. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfejsu w widoku, więc w edytorze można włączać i wyłączać elementów w **przybornika**.

    3. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> i wywołać `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> usługę, aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfejsów.

         Kroki te włączają Twojego pakietu VSPackage do dodawania nowych elementów do **przybornika**.

10. Zdecyduj, czy mają inne funkcje opcjonalne tego edytora.

    - Jeśli chcesz, aby tego edytora, aby obsługiwać Znajdź i Zamień poleceń, zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.

    - Jeśli chcesz użyć okno narzędzia tworzącego konspekt dokumentu w edytorze, zaimplementować `IVsDocOutlineProvider`.

    - Jeśli chcesz użyć paska stanu w edytorze, zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> i wywołać `QueryService` dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> uzyskać wskaźnik do `IVsStatusBar`.

         Na przykład, edytor może wyświetlać wiersza / informacje o kolumnach, tryb wyboru (przesyłanie strumieniowe / polu) i tryb wstawiania (Wstaw / overstrike).

    - Jeśli chcesz, aby tego edytora, aby obsługiwać `Undo` polecenia zalecaną metodą jest użycie modelu menedżera cofania OLE. Jako alternatywę, może mieć uchwyt edytora `Undo` polecenia bezpośrednio.

11. Tworzenie rejestru informacje, w tym identyfikatory GUID dla pakietu VSPackage, menu, edytora i inne funkcje.

     Poniżej przedstawiono przykładowy kod, który możesz umieścić w swojej *.rgs* pliku skryptu pokazują, jak poprawnie zarejestrować edytora.

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

12. Implementowanie Obsługa pomocy kontekstowej.

     Ten krok pozwala do zapewnienia pomocy F1 i dynamiczna Pomoc okna obsługi dla elementów w edytorze. Aby uzyskać więcej informacji, zobacz [jak: Dostarczanie kontekstu edytory](../extensibility/how-to-provide-context-for-editors.md).

13. Udostępnianie z edytorem modelu obiektu automatyzacji poprzez implementację `IDispatch` interfejsu.

     Aby uzyskać więcej informacji, zobacz [Współtworzenie modelu automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Skuteczne programowanie

- Tworzone jest wystąpienie edytora, gdy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody. Jeśli Edytor obsługuje wiele widoków, `CreateEditorInstance` tworzy zarówno dane dokumentu, jak i obiektów widoku dokumentu. Jeśli obiekt danych dokumentu jest już otworzyć, inną niż null `punkDocDataExisting` wartość jest przekazywana do `IVsEditorFactory::CreateEditorInstance`. Wdrożenie fabryki edytora należy określić, czy istniejący obiekt danych dokumentu jest zgodny, wykonywanie zapytań dotyczących odpowiednich interfejsów na nim. Aby uzyskać więcej informacji, zobacz [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).

- Jeśli używasz uproszczone podejście osadzania, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu.

- Jeśli zdecydujesz się używać aktywacji w miejscu, należy zaimplementować następujące interfejsy:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > `IOleInPlaceComponent` Interfejs jest używany w celu uniknięcia scalania menu OLE 2.

   Twoje `IOleCommandTarget` implementacja obsługuje poleceń, takich jak **Wytnij**, **kopiowania**, i **Wklej**. Podczas implementowania `IOleCommandTarget`, zdecyduj, czy edytor wymaga własnej *vsct* plik, aby zdefiniować własne polecenia menu struktury lub jeśli implementuje on standardowe polecenia definiowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Zazwyczaj edytory użyć rozszerzenia menu środowiska IDE i zdefiniować własne paski narzędzi. Często jest jednak niezbędne dla edytora zdefiniować własne odpowiednie polecenia, oprócz używania zestaw standardowych poleceń środowiska IDE. Edytor musi zadeklarować standardowe polecenia używa, a następnie zdefiniować nowe polecenia, menu kontekstowe, najwyższego poziomu menu i paski narzędzi w *vsct* pliku. Jeśli aktywacja w miejscu utworzyć edytor, zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> i zdefiniuj menu i paski narzędzi edytora w *vsct* zamiast za pomocą scalania menu OLE 2 pliku.

- Aby zapobiec polecenia menu skupienia się w interfejsie użytkownika, należy używać istniejących poleceń w IDE przed inventing nowych poleceń. Udostępnione polecenia są zdefiniowane w *SharedCmdDef.vsct* i *ShellCmdDef.vsct*. Te pliki są instalowane domyślnie w podkatalogu VisualStudioIntegration\Common\Inc swoje [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalacji.

- `ISelectionContainer` można wyrazić zarówno pojedynczych i wielu opcji. Każdy wybrany obiekt jest implementowany jako `IDispatch` obiektu.

- Implementuje IDE `IOleUndoManager` jako usługi dostępne z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> lub jako obiekt, który może być utworzone za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Implementuje Twojego edytora `IOleUndoUnit` interfejsu dla każdego `Undo` akcji.

- Istnieją dwa miejsca niestandardowy Edytor może narazić obiektów automatyzacji:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Zobacz także
- [Współtworzenie modelu automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md)
- [Instrukcje: Dostarczanie kontekstu edytorów](../extensibility/how-to-provide-context-for-editors.md)