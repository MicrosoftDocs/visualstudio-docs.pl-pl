---
title: Podstawowe informacje o usłudze starszego języka | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88e2b07fe640c2b9c69259cfc9ec48d98594bd6f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795637"
---
# <a name="legacy-language-service-essentials"></a>Podstawowe informacje dotyczące starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Należy podać usługa języka, do integracji z językiem programowania w Visual Studio. W tym temacie opisano funkcje dostępne w usługach starszego języka.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi języka, zobacz [edytora i rozszerzenia usługi w języka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
 Usługi starszego języka zapewniają następujące funkcje:  
  
|Funkcja|Opis|  
|-------------|-----------------|  
|Kolorowanie składni|Powoduje, że widok edytora wyświetlić różne kolory i style dla różnych elementów języka. To zróżnicowanie może ułatwić na odczytywanie i edytowanie plików.<br /><br /> Aby uzyskać ogólne informacje, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Aby uzyskać informacje na temat tej funkcji w ramach pakietu zarządzanego (MPF), zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Uzupełnianie instrukcji|Wykonuje instrukcję lub słowo kluczowe, które użytkownik rozpoczął, wpisując. Uzupełnianie instrukcji pomaga użytkownikom łatwiejsze, wprowadź trudne instrukcji z mniej wpisywania i mniej prawdopodobieństwo, że błąd.<br /><br /> Aby uzyskać ogólne informacje, zobacz [uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Aby uzyskać informacji dotyczących tej funkcji w MPF, zobacz [uzupełnianie wyrazów w starszej wersji usługi językowej](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Parowanie nawiasów klamrowych|Najważniejsze funkcje sparowane znaków, takich jak nawiasy klamrowe. Gdy użytkownik wpisuje znak zamykającego takich jak "}", parowanie nawiasów klamrowych wyróżnia odpowiadającego otwierania znaków, takich jak "{". Gdy istnieje kilka poziomów otaczającej znaków, ta funkcja pomaga użytkownikom, upewnij się, że otaczającego znaki są poprawnie połączone w pary.<br /><br /> Aby uzyskać informacji dotyczących tej funkcji w MPF, zobacz [parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Etykietki narzędzi informacji parametru|Wyświetla listę możliwych podpisów dla przeciążonej metody wpisywany przez użytkownika.<br /><br /> Aby uzyskać ogólne informacje, zobacz [o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Aby uzyskać informacji dotyczących tej funkcji w MPF, zobacz [o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Znaczniki błędów|Wyświetla czerwoną linią falistą, znany także jako falista pod tekstem, który jest nieprawidłowy. Znaczniki błędów są zwykle używane do uświadomić użytkowników błędnie napisane słowa kluczowe, niezamknięty nawias, nieprawidłowe znaki i podobne błędy.<br /><br /> W klasach MPF znaczniki błędów są obsługiwane automatycznie w <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metody <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy.|  
  
 Wiele z tych funkcji wymaga usługi językowej do analizowania kodu źródłowego. Często można wykorzystać analizowania kodu dla kompilatora lub interpretera i tokenizowanie.  
  
 Następujące funkcje są związaną z pomocą techniczną dla języków programowania, ale nie są częścią usług językowych:  
  
|Funkcja|Opis|  
|-------------|-----------------|  
|Ewaluatory wyrażeń|Obsługuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugera, sprawdzanie poprawności punktów przerwania i przekazując lista wyrażeń do wyświetlenia w **Autos** okna debugowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [Obsługa usługi językowej do debugowania](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Narzędzia do przeglądania symboli|Obsługuje **przeglądarka obiektów**, **Widok klas**, **przeglądarka wywołań**, i **wyniki Znajdź Symbol**.|
