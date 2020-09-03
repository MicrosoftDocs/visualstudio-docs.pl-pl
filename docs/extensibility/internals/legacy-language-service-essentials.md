---
title: Wersja podstawowa usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707424"
---
# <a name="legacy-language-service-essentials"></a>Podstawowe informacje dotyczące starszej wersji usługi językowej
Musisz podać usługę językową, aby zintegrować język programowania w programie Visual Studio. W tym temacie opisano funkcje dostępne w starszych usługach językowych.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [edytory i rozszerzenia usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

 Starsze usługi językowe zapewniają następujące funkcje:

|Cechy|Opis|
|-------------|-----------------|
|Kolorowanie składni|Powoduje, że widok edytora wyświetla różne kolory i style czcionek dla różnych elementów języka. Takie rozróżnienie może ułatwić odczytywanie i edytowanie plików.<br /><br /> Aby uzyskać ogólne informacje, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Aby uzyskać informacje na temat tej funkcji w programie Managed Package Framework (MPF), zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Uzupełnianie instrukcji|Kończy instrukcję lub słowo kluczowe, które rozpoczęło wpisywanie przez użytkownika. Uzupełnianie instrukcji ułatwia użytkownikom wprowadzanie trudnych instrukcji w łatwiejszy sposób, z mniejszą literą i mniejszą liczbą błędów.<br /><br /> Aby uzyskać ogólne informacje, zobacz [uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Aby uzyskać informacje na temat tej funkcji w MPF, zobacz [uzupełnianie wyrazów w starszej wersji usługi językowej](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Dopasowywanie nawiasów klamrowych|Wyróżnia znaki sparowane, takie jak nawiasy klamrowe. Gdy użytkownik wpisze znak zamykający, taki jak "}", dopasowywanie nawiasów klamrowych podświetla odpowiedni znak otwarcia, taki jak "{". Jeśli istnieje kilka poziomów otaczających znaków, ta funkcja pomaga użytkownikom potwierdzić, że otaczające znaki są poprawnie sparowane.<br /><br /> Aby uzyskać informacje na temat tej funkcji w MPF, zobacz [nawiasy klamrowe w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Etykietki narzędzi informacji o parametrach|Wyświetla listę możliwych sygnatur dla przeciążonej metody, która jest aktualnie wpisywana przez użytkownika.<br /><br /> Aby uzyskać ogólne informacje, zobacz [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Aby uzyskać informacje na temat tej funkcji w MPF, zobacz [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Znaczniki błędów|Wyświetla czerwoną falistą podkreślenie, znaną również jako falistej, w obszarze tekst, który jest syntaktycznie niepoprawny. Znaczniki błędów są zwykle używane do udostępniania użytkownikom błędnie napisanych słów kluczowych, niezamkniętych nawiasów, nieprawidłowych znaków i podobnych błędów.<br /><br /> W klasach MPF znaczniki błędów są obsługiwane automatycznie w <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodzie <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy.|

 Wiele z tych funkcji wymaga, aby usługa języka mogła analizować kod źródłowy. Często można ponownie wykorzystać tokenizowanie i analizę kodu dla kompilatora lub interpretera.

 Następujące funkcje są związane z obsługą języków programowania, ale nie są częścią usług językowych:

| Cechy | Opis |
|-----------------------| - |
| Ocenianie wyrażeń | Obsługuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debuger, sprawdzając poprawność punktów przerwania i dostarczając listę wyrażeń, które mają być wyświetlane **Autos** w oknie Debugowanie.<br /><br /> Aby uzyskać więcej informacji, zobacz [Obsługa języka na potrzeby debugowania](../../extensibility/internals/language-service-support-for-debugging.md). |
| Narzędzia do przeglądania symboli | Obsługuje **Przeglądarka obiektów**, **Widok klasy**, **przeglądarka wywołań**i **Znajdź wyniki symboli**. |
