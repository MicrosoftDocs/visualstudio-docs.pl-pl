---
title: Tworzenie niestandardowych edytorów i projektantów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a806e434bebb5a561534fb8aec19d16dc9e28ffd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891048"
---
# <a name="create-custom-editors-and-designers"></a>Tworzenie niestandardowych edytorów i projektantów

Visual Studio zintegrowane środowisko programistyczne (IDE) mogą obsługiwać różne rodzaje Edytor:

- Podstawowy edytor programu Visual Studio

- Edytorach niestandardowych

- Edytory zewnętrzne

- Projektanci

Poniższe informacje pomaga wybrać typu edytora, których potrzebujesz.

## <a name="types-of-editor"></a>Typy edytora

Aby uzyskać informacji na temat podstawowy edytor programu Visual Studio, zobacz [rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Edytorach niestandardowych
 Niestandardowego edytora jest taki, który jest przeznaczony do pracy w specjalne okoliczności. Na przykład może utworzyć edytor, którego funkcja jest do odczytu i zapisu danych do określonego repozytorium, takich jak Microsoft Exchange server. Wybierz niestandardowy edytor, jeśli chcesz, aby Edytor który współdziała z danego typu projektu, lub jeśli chcesz, aby edytor, który ma kilka konkretnych poleceń. Należy jednak pamiętać, że użytkownicy nie będą mogli używać niestandardowego edytora do edycji standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektów.

 Niestandardowy Edytor użyć fabryki edytora i Dodaj informacje o Edytorze do rejestru. Jednakże typ projektu, skojarzony z edytora niestandardowego można utworzyć wystąpienie edytora niestandardowego w inny sposób.

 Niestandardowy edytor, można użyć aktywacji w miejscu lub uproszczone osadzanie do zaimplementowania widoku.

### <a name="external-editors"></a>Edytory zewnętrzne
 Edytory zewnętrzne są edytory, które nie są zintegrowane z Visual Studio, takich jak Microsoft Word, program Notatnik lub program Microsoft FrontPage. Jeśli, na przykład, przekazujesz tekstu do niego z Twojego pakietu VSPackage, może wywołać takich edytora. Edytory zewnętrzne rejestrują się i mogą być używane poza programem Visual Studio. Gdy wywołujesz edytor zewnętrzny i mogą być osadzone w oknie hosta, następnie pojawi się on okna w IDE. Jeśli nie, następnie tworzy osobne okno środowiska IDE dla niego.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Metody Ustawia priorytet dokumentu przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wyliczenia. Jeśli `DP_External` jest określona, plik może otworzyć zewnętrznego edytora.

## <a name="editor-design-decisions"></a>Decyzje dotyczące projektu w edytorze
 Na następujące pytania projekt ułatwią wybierz typ edytora najlepiej nadaje się do aplikacji:

- Aplikacja zapisze dane w plikach czy nie? Jeśli będzie zapisywał dane w plikach, będą one w formacie niestandardowych lub standardowych?

   Jeśli używasz formatu standardowego pliku, innych typów projektów, oprócz projektu będzie można otworzyć i odczytu/zapisu danych do nich. Jeśli używasz formatu niestandardowego pliku, jednak tylko typ projektu będzie do otwierania i odczytu/zapisu danych do nich.

   Jeśli projekt używa plików, należy dostosować standardowy edytor. Jeśli projekt nie korzysta z plików, ale raczej używa elementów w bazie danych lub w innym repozytorium, należy utworzyć niestandardowy Edytor.

- Czy edytor potrzebuje do hostowania kontrolki ActiveX?

   Jeśli Edytor obsługuje formanty ActiveX, implementować edytora aktywacji w miejscu, co zostało opisane w [Aktywacja w miejscu](../extensibility/in-place-activation.md). Jeśli nie obsługuje kontrolki ActiveX, następnie użyj uproszczony Edytor osadzania lub dostosować [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] domyślnego edytora.

- Edytor obejmie wiele widoków? Musi obsługiwać wiele widoków, jeśli chcesz, aby widoki tego edytora, aby być widoczne w tym samym czasie jako domyślny edytor.

   Jeśli Edytor musi obsługiwać wiele widoków, dane dokumentu i dokumentu obiektów widoku edytora musi być oddzielnych obiektach. Aby uzyskać więcej informacji, zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).

   Jeśli Edytor obsługuje wiele widoków, czy zamierzasz używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podstawowe implementację buforu tekstu edytora (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektów) dla obiektu danych dokumentu? Oznacza to, że chcesz obsługiwać usługi Edytor widoku side-by-side przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytorze podstawowych funkcji? W tym celu jest podstawą projektanta formularzy...

- Jeśli musisz hostować edytor zewnętrzny edytor można osadzić wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?

   Jeśli mogą być osadzone, należy utworzyć okno hosta zewnętrznego edytora, a następnie wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metody i ustaw <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wartość wyliczenia do `DP_External`. Jeśli Edytor nie może zostać osadzony, IDE automatycznie utworzy oddzielne okno dla niego.

## <a name="in-this-section"></a>W tej sekcji

[Przewodnik: Tworzenie niestandardowego edytora](../extensibility/walkthrough-creating-a-custom-editor.md)\
Wyjaśnia, jak utworzyć niestandardowy Edytor.

[Przewodnik: Dodawanie funkcji do edytora niestandardowego](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Opis sposobu dodawania funkcji do edytora niestandardowego.

[Projektanta konfiguracji inicjowania i metadane](../extensibility/designer-initialization-and-metadata-configuration.md)\
Wyjaśnia, jak zainicjować projektanta.

[Podaj Obsługa polecenia Cofnij do projektantów](../extensibility/supplying-undo-support-to-designers.md)\
Wyjaśnia sposób zapewnienia Obsługa polecenia Cofnij do projektantów.

[Kolorowanie składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)\
Wyjaśnia różnicę pomiędzy kolorowania w edytorze podstawowych i w edytorach niestandardowych.

[Dane dokumentu i Widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Wyjaśnia, jak wdrażać danych dokumentów i widoków dokumentu w edytorach niestandardowych.

## <a name="related-sections"></a>Sekcje pokrewne

[Interfejsy starszej wersji w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)\
Wyjaśnia, jak uzyskać dostęp podstawowy edytor za pomocą starszej wersji interfejsu API.

[Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)\
Wyjaśnia, jak zaimplementować usługę języka.

[Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Wyjaśnia, jak utworzyć elementy interfejsu użytkownika, zgodne z pozostałą część [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>