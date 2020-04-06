---
title: Rozszerzenie usługi językowej w celu obsługi editorconfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699582"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Obsługa EditorConfig dla usługi językowej

[EditorConfig](https://editorconfig.org/) pliki umożliwiają opisanie typowych opcji edytora tekstu, takich jak rozmiar wcięcie, na podstawie projektu. Aby dowiedzieć się więcej o obsłudze plików EditorConfig w programie Visual Studio, zobacz [Tworzenie ustawień edytora przenośnego przy użyciu funkcji EditorConfig](../ide/create-portable-custom-editor-options.md).

W większości przypadków podczas implementowania usługi języka Visual Studio nie jest wymagana żadna dodatkowa praca do obsługi Właściwości uniwersalne EditorConfig. Edytor podstawowy automatycznie odnajduje i odczytuje plik .editorconfig, gdy użytkownicy otwierają pliki, a także ustawia odpowiednie opcje buforu tekstu i widoku. Jednak w przypadku zmian, takich jak karty i spacje, niektóre usługi językowe decydują się na użycie odpowiedniej opcji kontekstowego widoku tekstu zamiast ustawień globalnych. W takich przypadkach usługa języka musi zostać zaktualizowana do obsługi plików EditorConfig.

Poniżej przedstawiono zmiany, które są potrzebne do aktualizacji usługi języka do obsługi plików EditorConfig, zastępując globalną opcję _specyficzne dla języka_ z opcją _kontekstową:_

## <a name="indent-style"></a>Styl wcięcie

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fNaty z napisami<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|Domena !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>Domena widok.opcje.opcje.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Rozmiar wcięcie

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Rozmiar karty

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Zobacz też

- [Tworzenie ustawień edytora przenośnego przy użyciu funkcji EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Rozszerzanie usług edytora i językowych](../extensibility/extending-the-editor-and-language-services.md)
