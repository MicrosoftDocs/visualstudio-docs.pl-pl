---
title: Ukończenie programu Word w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703175"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Uzupełnianie wyrazów w starszej wersji usługi językowej
Uzupełnianie wyrazu wypełnia brakujące znaki w częściowo wpisanym słowie. Jeśli istnieje tylko jedno możliwe zakończenie, słowo jest wypełniane po wprowadzeniu znaku zakończenia. Jeśli słowo częściowe pasuje do więcej niż jednej możliwości, zostanie wyświetlona lista możliwych uzupełnień. Znak uzupełniania może być dowolnym znakiem, który nie jest używany dla identyfikatorów.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="implementation-steps"></a>Etapy wdrażania

1. Gdy użytkownik wybierze **opcję Zakończ program Word** z menu **IntelliSense,** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenie jest wysyłane do usługi językowej.

2. Klasa <xref:Microsoft.VisualStudio.Package.ViewFilter> łapie polecenie i <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> wywołuje metodę z powodu <xref:Microsoft.VisualStudio.Package.ParseReason>analizy .

3. Klasa <xref:Microsoft.VisualStudio.Package.Source> następnie wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę, aby uzyskać listę możliwych uzupełnień wyrazów, a następnie <xref:Microsoft.VisualStudio.Package.CompletionSet> wyświetla wyrazy na liście porad narzędzia przy użyciu klasy.

    Jeśli istnieje tylko jeden pasujący wyraz, <xref:Microsoft.VisualStudio.Package.Source> klasa uzupełnia wyraz.

   Alternatywnie, jeśli skaner zwraca <xref:Microsoft.VisualStudio.Package.TokenTriggers> wartość wyzwalacza po wpisaniu pierwszego znaku <xref:Microsoft.VisualStudio.Package.Source> identyfikatora, klasa <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> wykrywa to i wywołuje <xref:Microsoft.VisualStudio.Package.ParseReason>metodę z powodu analizy . W takim przypadku analizator musi wykryć obecność znaku wyboru elementu członkowskiego i podać listę elementów członkowskich.

## <a name="enabling-support-for-the-complete-word"></a>Włączanie obsługi kompletnego programu Word
 Aby włączyć obsługę zakończenia `CodeSense` słowa, ustawiono <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> nazwany parametr przekazany do atrybutu użytkownika skojarzonego z pakietem językowym. Spowoduje to <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> ustawienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences> właściwości na klasę.

 Analizator musi zwrócić listę deklaracji w odpowiedzi na wartość <xref:Microsoft.VisualStudio.Package.ParseReason>przyczyny analizy , aby zakończyć działanie wyrazów.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementowanie pełnego programu Word w metodzie ParseSource
 W przypadku uzupełniania wyrazów <xref:Microsoft.VisualStudio.Package.Source> klasa wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodę w klasie, <xref:Microsoft.VisualStudio.Package.AuthoringScope> aby uzyskać listę możliwych dopasowań wyrazów. Należy zaimplementować listę w klasie, <xref:Microsoft.VisualStudio.Package.Declarations> która pochodzi od klasy. Zobacz <xref:Microsoft.VisualStudio.Package.Declarations> klasy szczegółowe informacje na temat metod, które należy zaimplementować.

 Jeśli lista zawiera tylko jedno słowo, <xref:Microsoft.VisualStudio.Package.Source> klasa automatycznie wstawia to słowo zamiast wyrazu częściowego. Jeśli lista zawiera więcej niż <xref:Microsoft.VisualStudio.Package.Source> jedno słowo, klasa przedstawia listę porad narzędzi, z których użytkownik może wybrać odpowiedni wybór.

 Również spojrzeć na <xref:Microsoft.VisualStudio.Package.Declarations> przykład implementacji klasy w [ukończeniu elementu członkowskiego w usłudze języka starszego](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
