---
title: Tworzenie niestandardowych edytorów i projektantów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739475"
---
# <a name="create-custom-editors-and-designers"></a>Tworzenie niestandardowych edytorów i projektantów

Zintegrowane środowisko programistyczne programu Visual Studio (IDE) może obsługiwać różne typy edytora:

- Edytor podstawowy programu Visual Studio

- Edytory niestandardowe

- Redaktorzy zewnętrzni

- Projektanci

Poniższe informacje ułatwią wybór typu edytora, którego potrzebujesz.

## <a name="types-of-editor"></a>Typy edytora

Aby uzyskać informacje na temat edytora podstawowego programu Visual Studio, zobacz [Rozszerzanie usług edytora i języków](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Edytory niestandardowe
 Edytor niestandardowy jest taki, który jest przeznaczony do pracy w wyspecjalizowanych okolicznościach. Na przykład można utworzyć edytor, którego funkcją jest odczyt i zapis danych do określonego repozytorium, takiego jak serwer Microsoft Exchange. Wybierz edytor niestandardowy, jeśli chcesz edytor, który działa tylko z typem projektu lub jeśli chcesz edytor, który ma tylko kilka określonych poleceń. Należy jednak pamiętać, że użytkownicy nie będą mogli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytować standardowych projektów za pomocą edytora niestandardowego.

 Edytor niestandardowy może używać fabryki edytora i dodawać informacje o edytorze do rejestru. Jednak typ projektu skojarzony z edytorem niestandardowym można utworzyć wystąpienia edytora niestandardowego w inny sposób.

 Edytor niestandardowy może używać aktywacji w miejscu lub uproszczonego osadzania w celu zaimplementowania widoku.

### <a name="external-editors"></a>Edytory zewnętrzne
 Edytory zewnętrzne to edytory, które nie są zintegrowane z programem Visual Studio, takie jak Microsoft Word, Notatnik lub program Microsoft FrontPage. Można wywołać takiego edytora, jeśli, na przykład, przekazujesz tekst do niego z VSPackage. Zewnętrzni redaktorzy rejestrują się i mogą być używane poza programem Visual Studio. Po wywołaniu edytora zewnętrznego i może być osadzony w oknie hosta, a następnie pojawia się w oknie w IDE. Jeśli nie, ide tworzy oddzielne okno dla niego.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> ustawia priorytet dokumentu przy <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> użyciu wyliczenia. Jeśli `DP_External` wartość jest określona, plik może zostać otwarty przez edytor zewnętrzny.

## <a name="editor-design-decisions"></a>Decyzje dotyczące projektowania edytora
 Następujące pytania projektowe pomogą Ci wybrać typ edytora najlepiej dopasowany do twojej aplikacji:

- Czy aplikacja zapisze swoje dane w plikach, czy nie? Jeśli zapisze swoje dane w plikach, będą one w formacie niestandardowym lub standardowym?

   Jeśli używasz standardowego formatu pliku, inne typy projektów oprócz projektu będą mogły otwierać i odczytywać/zapisywać dane. Jeśli jednak używasz niestandardowego formatu pliku, tylko typ projektu będzie mógł otwierać i odczytywać/zapisywać dane.

   Jeśli projekt używa plików, należy dostosować standardowy edytor. Jeśli projekt nie używa plików, ale raczej używa elementów w bazie danych lub innym repozytorium, należy utworzyć edytor niestandardowy.

- Czy edytor musi obsługiwać formanty ActiveX?

   Jeśli edytor obsługuje formanty ActiveX, zaimplementuj edytor aktywacji w miejscu, zgodnie z opisem [w pliku Aktywacja w miejscu.](/visualstudio/misc/in-place-activation?view=vs-2015) Jeśli nie obsługuje formantów ActiveX, użyj uproszczonego edytora osadzania lub dostosuj edytor domyślny. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

- Czy edytor obsługuje wiele widoków? Musisz obsługiwać wiele widoków, jeśli chcesz, aby widoki edytora były widoczne w tym samym czasie co edytor domyślny.

   Jeśli edytor musi obsługiwać wiele widoków, obiekty widoku danych dokumentu i dokumentu dla edytora muszą być oddzielnymi obiektami. Aby uzyskać więcej informacji, zobacz [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).

   Jeśli edytor obsługuje wiele widoków, czy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zamierzasz użyć implementacji<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> buforu tekstowego edytora core (obiektu) dla obiektu danych dokumentu? Oznacza to, że chcesz obsługiwać widok edytora obok [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] siebie z edytorem rdzenia? Możliwość tego jest podstawą projektanta formularzy..

- Jeśli potrzebujesz hosta zewnętrznego edytora, czy edytor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]może być osadzony w środku?

   Jeśli można go osadzać, należy utworzyć okno hosta dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> edytora <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> zewnętrznego, a następnie `DP_External`wywołać metodę i ustawić wartość wyliczenia na . Jeśli edytor nie może być osadzony, IDE automatycznie utworzy dla niego oddzielne okno.

## <a name="in-this-section"></a>W tej sekcji

[Przewodnik: Tworzenie edytora niestandardowego](../extensibility/walkthrough-creating-a-custom-editor.md)\
W tym artykule wyjaśniono, jak utworzyć edytor niestandardowy.

[Przewodnik: Dodawanie funkcji do edytora niestandardowego](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
W tym artykule wyjaśniono, jak dodać funkcje do edytora niestandardowego.

[Inicjowanie projektanta i konfiguracja metadanych](../extensibility/designer-initialization-and-metadata-configuration.md)\
W tym artykule wyjaśniono, jak zainicjować projektanta.

[Dostarczanie wsparcia cofania dla projektantów](../extensibility/supplying-undo-support-to-designers.md)\
W tym artykule wyjaśniono, jak zapewnić obsługę cofania dla projektantów.

[Kolorowanie składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)\
Wyjaśnia różnicę między kolorowanie składni w edytorze podstawowym i w edytorach niestandardowych.

[Wyświetlanie danych i dokumentów w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)\
W tym artykule wyjaśniono, jak zaimplementować widoki danych dokumentów i dokumentów w edytorach niestandardowych.

## <a name="related-sections"></a>Powiązane sekcje

[Starsze interfejsy w edytorze](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
W tym artykule wyjaśniono, jak uzyskać dostęp do edytora podstawowego za pomocą starszego interfejsu API.

[Tworzenie starszej usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)\
W tym artykule wyjaśniono, jak zaimplementować usługę językową.

[Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
W tym artykule wyjaśniono, jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]utworzyć elementy interfejsu użytkownika, które pasują do reszty programu .

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
