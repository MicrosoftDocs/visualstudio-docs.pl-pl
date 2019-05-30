---
title: Rozszerzanie usługi językowej do obsługi polecenia EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be9502569fd57da630da949ba14bbfc5e9045a22
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261816"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Obsługa wtyczki EditorConfig dla usługi w języka

[Polecenie EditorConfig](http://editorconfig.org/) pliki umożliwiają opisano typowe opcje edytora tekstu, takie jak rozmiar wcięcia w poszczególnych projektów. Aby dowiedzieć się więcej na temat obsługi programu Visual Studio dla plików EditorConfig, zobacz [utworzyć ustawienia edytora przenośne przy użyciu pliku EditorConfig](../ide/create-portable-custom-editor-options.md).

W większości przypadków podczas implementowania usługi języka programu Visual Studio, żadne dodatkowe czynności jest wymagane do obsługi EditorConfig universal właściwości. Podstawowy edytor automatycznie wykrywa i odczytuje plik .editorconfig, gdy użytkownicy otwierają pliki i ustawia odpowiedni tekst w buforze i wyświetlanie opcji. Jednak do edycji, takie jak znaki tabulacji i spacje, niektóre usługi w języka zdecydować się na użycie odpowiedni tekst kontekstowe widoku opcji, a nie przy użyciu ustawień globalnych. W takich przypadkach usługa językowa musi zostać zaktualizowany do obsługi plików EditorConfig.

Poniżej przedstawiono zmiany, które są niezbędne do aktualizowania usługi język do obsługi plików EditorConfig, zastępując globalną _specyficzny dla języka_ z opcją _kontekstowych_ opcji:

## <a name="indent-style"></a>Styl wcięcia

Opcje specyficzne dla języka | Opcje kontekstowych
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Wcięcie

Opcje specyficzne dla języka | Opcje kontekstowych
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Rozmiar tabulatora

Opcje specyficzne dla języka | Opcje kontekstowych
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Zobacz także

- [Utwórz ustawienia edytora przenośne przy użyciu pliku EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md)