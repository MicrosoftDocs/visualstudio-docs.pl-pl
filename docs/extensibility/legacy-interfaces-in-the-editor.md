---
title: Interfejsy starszej wersji w edytorze | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 044bf36845be70290291b79dee255c452f56f0a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907477"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfejsy starszej wersji w edytorze
Edytor programu Visual Studio dostęp ze starszych interfejsów. Visual Studio SDK zawiera kart znanych jako *podkładki*, umożliwiają one te interfejsy do interakcji z nowego edytora. Niemniej jednak zaleca się zaktualizowanie starszej wersji kodu, aby użyć nowego edytora interfejsu API. Twój kod będzie działać lepiej i można użyć nowych technologii, takich jak Windows Presentation Foundation (WPF) i Managed Extensibility Framework (MEF).

## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| - | - |
| [Dostosowanie starszego kodu do edytora](../extensibility/adapting-legacy-code-to-the-editor.md) | Wyjaśnia, jak dostosować swój kod, aby nowego edytora. |
| [Zachowaniem nowe lub zostały zmienione z kartami edytora](../extensibility/new-or-changed-behavior-with-editor-adapters.md) | W tym artykule wyjaśniono, jak zachowanie kart edytora różni się od wcześniejszych wersjach edytora. |
| [W edytorze podstawowych](../extensibility/inside-the-core-editor.md) | W tym artykule opisano różne składniki wcześniejszych wersjach edytora. |
| [Utwórz wystąpienie podstawowy edytor przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) | Wyjaśnia, jak utworzyć podstawowy edytor za pomocą starszej wersji interfejsu API. |
| [Fabryki edytora](../extensibility/editor-factories.md) | Wyjaśnia, jak fabryki edytora za pomocą starszej wersji interfejsu API. |
| [Instrukcje: Zarejestruj Edytor typów plików](../extensibility/how-to-register-editor-file-types.md) | Wyjaśnia, jak połączyć z rozszerzeniem nazwy pliku do edytora. |
| [Przewodnik: Tworzenie podstawowej edytora i zarejestrować typ pliku edytora](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) | Wyjaśnia sposób tworzenia podstawowej edytora i połączyć rozszerzenie nazwy pliku. |
| [Instrukcje: Dostarczanie kontekstu edytorów](../extensibility/how-to-provide-context-for-editors.md) | Wyjaśnia, jak zapewnić kontekst tego edytora. |
| [Usługi języka oraz podstawowy edytor](../extensibility/language-services-and-the-core-editor.md) | W tym artykule wyjaśniono, interakcji między usługi językowej i edytora. |
| [Dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) | Wyjaśnia, jak dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API. |
| [Wyświetl theText dostępu przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) | Wyjaśnia, jak dostęp do widoku tekstu przy użyciu starszej wersji interfejsu API. |
| [Dostosowywanie kodu systemu windows przy użyciu starszej wersji interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) | Opis sposobu dostosowywania kodu systemu windows przy użyciu starszej wersji interfejsu API. |
| [Dostęp do warstwy tekstu przy użyciu starszej wersji interfejsu API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md) | Wyjaśnia, jak dostęp do różnych warstw tekstu przy użyciu starszej wersji interfejsu API. |
| [Korzystanie ze znaczników tekstu przy użyciu starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md) | Wyjaśnia, jak dodać znaczniki tekstu przy użyciu starszej wersji interfejsu API. |
| [Dostosowywanie menu i formantów w edytorze przy użyciu starszej wersji interfejsu API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md) | Wyjaśnia, jak dostosować formanty edytora przy użyciu starszej wersji interfejsu API. |
| [Zarządzanie Cofnij i wykonaj ponownie przy użyciu starszej wersji interfejsu API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md) | Wyjaśnia, jak zarządzać Cofnij i wykonaj ponownie przy użyciu starszej wersji interfejsu API. |
| [Instrukcje: Implementowanie Znajdź i Zamień mechanizm](../extensibility/how-to-implement-the-find-and-replace-mechanism.md) | Wyjaśnia, jak zarządzać Znajdź i Zamień przy użyciu starszej wersji interfejsu API. |
| [Instrukcje: Pomiń powiadomienia o zmianie pliku](../extensibility/how-to-suppress-file-change-notifications.md) | Wyjaśnia, jak wyłączyć powiadomienia o zmianie pliku przy użyciu starszej wersji interfejsu API. |
| [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md) | Wyjaśnia sposób tworzenia niestandardowych edytorów i projektantów. |
| [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md) | Zawiera łącza do dokumentów o funkcjach, które zapewniają możliwość dostosowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytorze podstawowych funkcji przez dodanie obsługi dla usługi w języka. |
| [Używanie czcionek i kolorów](../extensibility/using-fonts-and-colors.md) | Opis sposobu użycia czcionki i kolory z interfejsami starszej wersji. |
