---
title: Uzupełnianie wyrazów w starszej wersji usługi językowej | Microsoft Docs
description: Uzupełnianie wyrazów może być obsługiwane w przypadku starszej wersji usługi językowej w zestawie SDK programu Visual Studio. Dowiedz się, jak starsze usługi językowe są zaimplementowane w pakietu VSPackage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 489b43c825e3512e1bd33bc732833de84aed54c3
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616278"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Uzupełnianie wyrazów w starszej wersji usługi językowej
Uzupełnianie wyrazów wypełnia brakujące znaki w częściowo określonym słowie. Jeśli istnieje tylko jedno możliwe zakończenie, słowo zostanie zakończone po wprowadzeniu znaku uzupełniania. Jeśli częściowy wyraz jest zgodny z więcej niż jedną możliwością, zostanie wyświetlona lista możliwych uzupełnień. Znak uzupełniania może być dowolnym znakiem, który nie jest używany do identyfikatorów.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="implementation-steps"></a>Kroki implementacji

1. Po wybraniu przez użytkownika **kompletnego słowa** z menu **IntelliSense** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenie jest wysyłane do usługi językowej.

2. <xref:Microsoft.VisualStudio.Package.ViewFilter>Klasa przechwytuje polecenie i wywołuje <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodę z powodu analizy <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. <xref:Microsoft.VisualStudio.Package.Source>Następnie Klasa wywołuje metodę, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Aby uzyskać listę możliwych uzupełnień wyrazów, a następnie wyświetla słowa na liście etykietki narzędzia przy użyciu <xref:Microsoft.VisualStudio.Package.CompletionSet> klasy.

    Jeśli istnieje tylko jeden pasujący wyraz, <xref:Microsoft.VisualStudio.Package.Source> Klasa ukończy wyraz.

   Alternatywnie, jeśli skaner zwraca wartość wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> , gdy jest wpisywany pierwszy znak identyfikatora, <xref:Microsoft.VisualStudio.Package.Source> Klasa wykrywa to i wywołuje <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodę z powodu analizy <xref:Microsoft.VisualStudio.Package.ParseReason> . W takim przypadku analizator musi wykryć obecność znaku wyboru elementu członkowskiego i podać listę elementów członkowskich.

## <a name="enabling-support-for-the-complete-word"></a>Włączanie obsługi kompletnego wyrazu
 Aby włączyć obsługę zestawu do uzupełniania wyrazów, `CodeSense` nazwany parametr przesłany do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu użytkownika skojarzonego z pakietem języka. Powoduje to ustawienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.

 Analizator musi zwrócić listę deklaracji w odpowiedzi na wartość przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason> dla uzupełniania wyrazu do działania.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementowanie kompletnego wyrazu w metodzie ParseSource
 W przypadku uzupełniania słów <xref:Microsoft.VisualStudio.Package.Source> Klasa wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodę <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy, aby uzyskać listę możliwych dopasowań programu Word. Należy zaimplementować listę w klasie, która jest pochodną <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Zapoznaj się z <xref:Microsoft.VisualStudio.Package.Declarations> klasą, aby uzyskać szczegółowe informacje na temat metod, które należy zaimplementować.

 Jeśli lista zawiera tylko jeden wyraz, <xref:Microsoft.VisualStudio.Package.Source> Klasa automatycznie wstawia ten wyraz zamiast częściowego wyrazu. Jeśli lista zawiera więcej niż jeden wyraz, <xref:Microsoft.VisualStudio.Package.Source> Klasa przedstawia listę etykietki narzędzi, z której użytkownik może wybrać odpowiedni wybór.

 Zapoznaj się również z przykładem <xref:Microsoft.VisualStudio.Package.Declarations> implementacji klasy w [przypadku wykonania elementu członkowskiego w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
