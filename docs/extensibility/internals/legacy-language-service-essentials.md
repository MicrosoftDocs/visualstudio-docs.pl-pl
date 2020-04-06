---
title: Podstawowe usługi języka starszego | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707424"
---
# <a name="legacy-language-service-essentials"></a>Podstawowe informacje dotyczące starszej wersji usługi językowej
Należy zapewnić usługę języka, aby zintegrować język programowania z programem Visual Studio. W tym temacie opisano funkcje dostępne w starszych usługach językowych.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

 Starsze usługi językowe zapewniają następujące funkcje:

|Funkcja|Opis|
|-------------|-----------------|
|Kolorowanie składni|Powoduje, że widok edytora wyświetla różne kolory i style czcionek dla różnych elementów języka. To rozróżnienie może ułatwić odczytywanie i edytowanie plików.<br /><br /> Aby uzyskać ogólne informacje, zobacz [Kolorowanie składni w starszej usłudze językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Aby uzyskać informacje na temat tej funkcji w ramach pakietu zarządzanego (MPF), zobacz [Kolorowanie składni w starszej usłudze językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Uzupełnianie oświadczenia|Kończy instrukcję lub słowo kluczowe, które użytkownik rozpoczął wpisywanie. Uzupełnianie instrukcji ułatwia użytkownikom wprowadzanie trudnych instrukcji, mniej pisania i mniejsze szanse na błędy.<br /><br /> Aby uzyskać ogólne informacje, zobacz [Uzupełnianie instrukcji w starszej usłudze językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Aby uzyskać informacje na temat tej funkcji w mpf, zobacz [Zakończenie programu Word w starszej usłudze języka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Dopasowywanie nawiasów klamrowych|Wyróżnia sparowane znaki, takie jak nawiasy klamrowe. Gdy użytkownik wpisuje znak zamykający, taki jak "}", dopasowanie nawiasu klamrowego wyróżnia odpowiedni znak otwarcia, na przykład "{". Gdy istnieje kilka poziomów otaczających znaków, ta funkcja pomaga użytkownikom potwierdzić, że otaczające znaki są sparowane poprawnie.<br /><br /> Aby uzyskać informacje na temat tej funkcji w mpf, zobacz [Dopasowywanie nawiasów klamrowych w starszej usłudze języka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Etykietki narzędzi informacji o parametrach|Wyświetla listę możliwych podpisów dla przeciążona metoda, którą użytkownik aktualnie wpisuje.<br /><br /> Aby uzyskać ogólne informacje, zobacz [Informacje o parametrach w starszej usłudze językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Aby uzyskać informacje na temat tej funkcji w mpf, zobacz [Informacje o parametrach w starszej usłudze języka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Znaczniki błędów|Wyświetla faliste czerwone podkreślenie, znane również jako faliste, pod tekstem, który jest niepoprawny syntaktycznie. Znaczniki błędów są zwykle używane do uświadomienia użytkownikom błędnie napisanych słów kluczowych, niezamkniętych nawiasów, nieprawidłowych znaków i podobnych błędów.<br /><br /> W klasach MPF znaczniki błędów są <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> obsługiwane automatycznie <xref:Microsoft.VisualStudio.Package.AuthoringSink> w metodzie klasy.|

 Wiele z tych funkcji wymaga usługi języka do analizowania kodu źródłowego. Często można ponownie użyć tokenizacji i analizowania kodu dla kompilatora lub interpretera.

 Następujące funkcje są związane z obsługą języków programowania, ale nie są częścią usług językowych:

| Funkcja | Opis |
|-----------------------| - |
| Oceniający wyrażenia | Obsługuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugera, sprawdzając punkty przerwania i dostarczając listę wyrażeń, które mają być wyświetlane w oknie debugowania **autos.**<br /><br /> Aby uzyskać więcej informacji, zobacz [Obsługa usługi językowej dla debugowania](../../extensibility/internals/language-service-support-for-debugging.md). |
| Narzędzia do przeglądania symboli | Obsługuje **przeglądarkę obiektów,** **widok klasy,** **przeglądarkę połączeń**i znajdź wyniki **symboli**. |
