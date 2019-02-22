---
title: Wyraz uzupełniania w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f81895766a94bd22e533ead3078b3852ed68ca0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599853"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Uzupełnianie wyrazów w starszej wersji usługi językowej
Uzupełnianie wyrazów wypełnia brakujących znaków na częściowo wpisane programu word. Jeśli istnieje tylko jedno możliwe ukończenie, wyraz zostało zakończone, po wprowadzeniu znaku zakończenia. Jeśli wyrazów częściowych pasuje do więcej niż jedną z możliwości, zostanie wyświetlona lista możliwych ukończenia. Znak zakończenia może być dowolny znak, który nie jest używany dla identyfikatorów.

 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie usług edytora i języka](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.

## <a name="implementation-steps"></a>Kroki implementacji

1. Gdy użytkownik wybierze **Dokończ wyraz** z **IntelliSense** menu <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenia są wysyłane do usługi języka.

2. <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasy przechwytuje polecenia i wywołuje <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metoda przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason>.

3. <xref:Microsoft.VisualStudio.Package.Source> Klasę i wywołania <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę, aby uzyskać listę uzupełnienia możliwe programu word, a następnie wyświetla listę słów w etykietce narzędzia, za pomocą <xref:Microsoft.VisualStudio.Package.CompletionSet> klasy.

    Jeśli istnieje tylko jedno słowo dopasowania, <xref:Microsoft.VisualStudio.Package.Source> klasy kończy wyraz.

   Alternatywnie Jeśli skaner zwraca wartość wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> po wpisaniu pierwszy znak identyfikatora <xref:Microsoft.VisualStudio.Package.Source> klasy wykryje to i wywołuje <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metoda przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. W takim przypadku analizator musi wykryć obecność znaku wyboru elementu członkowskiego i zawierają listę elementów członkowskich.

## <a name="enabling-support-for-the-complete-word"></a>Włączanie obsługi Dokończ wyraz
 Aby włączyć obsługę zestawu ukończenia programu word `CodeSense` o nazwie parametr przekazany do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybut użytkownika skojarzonego z pakietem języka. To ustawienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.

 Twoje analizator musi zwracać listy deklaracji w odpowiedzi na wartość przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason>, do ukończenia programu word do działania.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementowanie Dokończ wyraz w metodzie ParseSource
 Do ukończenia programu word <xref:Microsoft.VisualStudio.Package.Source> klasy wywołania <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metody <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy, aby uzyskać listę word możliwych dopasowań. Listy należy zaimplementować w klasie, która jest pochodną <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Zobacz <xref:Microsoft.VisualStudio.Package.Declarations> klasy, aby uzyskać szczegółowe informacje na temat metody, należy zaimplementować.

 Jeśli lista zawiera tylko jeden wyraz, a następnie <xref:Microsoft.VisualStudio.Package.Source> klasy automatycznie wstawi słowo zamiast wyrazów częściowych. Jeśli lista zawiera więcej niż jeden wyraz <xref:Microsoft.VisualStudio.Package.Source> klasa przedstawia listę Porada narzędzia, z którego użytkownik może wybrać właściwy wybór.

 Także zapoznać się z przykładem <xref:Microsoft.VisualStudio.Package.Declarations> Implementacja klasy w [uzupełnianie składowych w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).