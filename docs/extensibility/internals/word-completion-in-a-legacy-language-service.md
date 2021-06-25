---
title: Uzupełnianie wyrazów w starszej wersji usługi językowej | Microsoft Docs
description: Uzupełnianie wyrazów może być obsługiwane w starszej wersji usługi językowej w Visual Studio SDK. Dowiedz się, jak starsze usługi językowe są implementowane w pakcie VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea386aea3a17b0fb0d93ff9872f92e86a166be5c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902634"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Uzupełnianie wyrazów w starszej wersji usługi językowej
Uzupełnianie wyrazów wypełnia brakujące znaki w częściowo wpisanym wyrazie. Jeśli istnieje tylko jedno możliwe ukończenie, wyraz zostanie ukończony po wprowadzeniu znaku ukończenia. Jeśli wyraz częściowy pasuje do więcej niż jednej możliwości, zostanie wyświetlona lista możliwych uzupełniania. Znak uzupełniania może być dowolnym znakiem, który nie jest używany dla identyfikatorów.

 Starsze usługi językowe są implementowane w ramach pakietów VSPackage, ale nowszą sposobem implementacji funkcji usługi językowej jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Rozszerzanie usług edytora i języka](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zalecamy jak najszybciej rozpocząć korzystanie z nowego interfejsu API edytora. Poprawi to wydajność usługi językowej i pozwoli korzystać z nowych funkcji edytora.

## <a name="implementation-steps"></a>Kroki implementacji

1. Gdy użytkownik wybierze pozycję **Complete Word (Ukończ wyraz)** z menu **IntelliSense,** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> polecenie zostanie wysłane do usługi językowej.

2. Klasa <xref:Microsoft.VisualStudio.Package.ViewFilter> przechwytuje polecenie i wywołuje metodę z przyczyną <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> analizy <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. Następnie klasa wywołuje metodę , aby uzyskać listę możliwych uzupełniania wyrazów, a następnie wyświetla wyrazy na liście etykietek <xref:Microsoft.VisualStudio.Package.Source> narzędzi przy użyciu klasy <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> .

    Jeśli istnieje tylko jeden zgodny wyraz, <xref:Microsoft.VisualStudio.Package.Source> klasa kończy to słowo.

   Alternatywnie, jeśli skaner zwraca wartość wyzwalacza po wpisaniu pierwszego znaku identyfikatora, klasa wykrywa ten błąd i wywołuje metodę z analizą <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source> przyczyny <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> . W takim przypadku parser musi wykryć obecność znaku wyboru składowej i podać listę elementów członkowskich.

## <a name="enabling-support-for-the-complete-word"></a>Włączanie obsługi pełnego wyrazu
 Aby włączyć obsługę uzupełniania wyrazów, ustaw `CodeSense` nazwany parametr przekazany do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu użytkownika skojarzonego z pakietem języka. W ten sposób <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> ustawiana jest właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy .

 Aby uzupełnianie wyrazów działało, parser musi zwrócić listę deklaracji w odpowiedzi na wartość przyczyny <xref:Microsoft.VisualStudio.Package.ParseReason> analizy .

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementowanie pełnego wyrazu w metodzie ParseSource
 W przypadku uzupełniania wyrazów klasa wywołuje metodę w klasie , <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> aby uzyskać listę <xref:Microsoft.VisualStudio.Package.AuthoringScope> możliwych dopasowania wyrazów. Należy zaimplementować listę w klasie pochodzącej od <xref:Microsoft.VisualStudio.Package.Declarations> klasy . Aby uzyskać <xref:Microsoft.VisualStudio.Package.Declarations> szczegółowe informacje na temat metod, które należy zaimplementować, zobacz klasę .

 Jeśli lista zawiera tylko jeden wyraz, klasa automatycznie wstawia ten wyraz w miejsce <xref:Microsoft.VisualStudio.Package.Source> częściowego wyrazu. Jeśli lista zawiera więcej niż jeden wyraz, klasa przedstawia listę etykietek narzędzi, z której użytkownik może <xref:Microsoft.VisualStudio.Package.Source> wybrać odpowiedni wybór.

 Przyjrzyj się również przykładowi implementacji klasy w <xref:Microsoft.VisualStudio.Package.Declarations> uzupełnianiu [członków w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
