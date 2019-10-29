---
title: Poszerzenie usługi językowej w celu obsługi EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 663a87ba15121896edcb4c049e7adc6b5c38492a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983107"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Obsługa EditorConfig dla usługi językowej

Pliki [EditorConfig](https://editorconfig.org/) umożliwiają opisywanie typowych opcji edytora tekstu, takich jak rozmiar wcięcia dla poszczególnych projektów. Aby dowiedzieć się więcej o obsłudze plików EditorConfig przez program Visual Studio, zobacz [Tworzenie ustawień przenośnego edytora przy użyciu EditorConfig](../ide/create-portable-custom-editor-options.md).

W większości przypadków podczas implementowania usługi językowej programu Visual Studio nie trzeba wykonywać żadnych dodatkowych czynności, aby obsługiwać właściwości uniwersalne EditorConfig. Podstawowy edytor automatycznie odnajduje i odczytuje plik. editorconfig, gdy użytkownicy otwierają pliki, i ustawia odpowiednie bufory tekstu i opcje wyświetlania. Jednak w przypadku edycji, takich jak karty i spacje, niektóre usługi językowe pomogą korzystać z odpowiedniej opcji widoku tekstu kontekstowego zamiast używać ustawień globalnych. W takich przypadkach należy zaktualizować usługę języka, aby obsługiwała pliki EditorConfig.

Poniżej przedstawiono zmiany, które są konieczne do zaktualizowania usługi językowej w celu obsługi plików EditorConfig, zastępując globalną opcję _specyficzną dla języka_ z opcją _kontekstową_ :

## <a name="indent-style"></a>Styl wcięcia

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. fInsertTabs<br/>Microsoft. VisualStudio. Package. LanguagePreferences. InsertTabs|! textBufferOptions. GetOption (DefaultOptions. ConvertTabsToSpacesOptionId)<br/>! textView. options. GetOption (DefaultOptions. ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Wcięcie rozmiaru

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. uIndentSize<br/>Microsoft. VisualStudio. Package. LanguagePreferences. InsertTabs. IndentSize|textBufferOptions. GetOption (DefaultOptions. IndentSizeOptionId)<br/>textView. options. GetOption (DefaultOptions. IndentSizeOptionId)

## <a name="tab-size"></a>Rozmiar karty

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. uTabSize<br/>Microsoft. VisualStudio. Package. LanguagePreferences. InsertTabs. TabSize|textBufferOptions. GetOption (DefaultOptions. TabSizeOptionId)<br/>textView. options. GetOption (DefaultOptions. TabSizeOptionId)

## <a name="see-also"></a>Zobacz także

- [Tworzenie ustawień edytora przenośnego za pomocą EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Rozszerzanie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md)