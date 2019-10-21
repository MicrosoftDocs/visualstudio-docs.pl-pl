---
title: Kompilowanie i tworzenie
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71bddf0f833bbaf717f7a2dbdf4a734efa295afb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619443"
---
# <a name="compiling-and-building-in-visual-studio"></a>Kompilowanie i kompilowanie w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można używać programu Visual Studio do kompilacji aplikacji i do tworzenia zestawów oraz programów wykonywalnych w krótkich odstępach czasu podczas cyklu rozwoju. Dzięki częstym kompilacjom kodu, można wcześniej wykryć błędy czasu kompilacji, takie jak niepoprawna składnia, błędnie napisane słowa kluczowe i niezgodności typów. Można także wykryć i poprawić błędy czasu wykonania, takie jak błędy logiczne i semantyczne, dzięki częstym kompilacjom i uruchamianiu wersji debugowania kodu.

 Kiedy projekt lub rozwiązanie jest już w pełni rozwinięte i zdebugowane, można skompilować jego składniki poprzez kompilację wydania. Domyślnie kompilacja wydania jest zoptymalizowana i zaprojektowana, aby była mniejsza i działała szybciej niż wersja do debugowania. Aby uzyskać więcej informacji, zobacz [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Wybieranie metody kompilacji
 Aplikację można skompilować za pomocą domyślnych opcji kompilacji w IDE, w wierszu polecenia lub przy użyciu Team Foundation Build. Każda z tych opcji używa programu MSBuild jako podstawowej technologii, a każde podejście ma określone korzyści, jak pokazano w poniższej tabeli.

|Metoda kompilacji|Zalety|Więcej informacji|
|------------------|--------------|--------------------------|
|Używanie IDE|— Możesz łatwiej tworzyć i uruchamiać kompilacje natychmiast.<br />— Można uruchamiać kompilacje wieloprocesorowe dla C++ programów C# i.<br />— Można dostosować niektóre aspekty systemu kompilacji.|[Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|Uruchomienie wiersza polecenia MSBuild|— Można kompilować projekty bez instalowania programu Visual Studio.<br />— W przypadku wszystkich typów projektów można uruchamiać kompilacje wieloprocesorowe.<br />— Można dostosować większość obszarów systemu kompilacji.|[MSBuild](../msbuild/msbuild.md)|
|Użycie Team Foundation Build|— Możesz zautomatyzować proces kompilacji. Można na przykład skompilować jeden lub więcej projektów w nocy lub za każdym razem, kiedy kod jest zaewidencjonowany. Można również kompilować projekty na udostępnionych serwerach kompilacji, a nie na komputerze dewelopera.<br />— Możesz szybko określić kod, który chcesz skompilować, testy, które chcesz uruchomić, oraz inne typowe opcje.<br />— Możesz zmodyfikować przepływ pracy kompilacji i w razie potrzeby utworzyć działania kompilacji, aby wykonywać głęboko dostosowane zadania.|[Kompilowanie aplikacji](/azure/devops/pipelines/index)|

## <a name="building-from-the-ide"></a>Kompilacja z IDE
 Podczas tworzenia projektu domyślne konfiguracje kompilacji zostają dla niego zdefiniowane, a konfiguracja kompilacji rozwiązania zostaje do niego przypisana, aby dostarczyć kontekst dla kompilacji. Konfiguracje rozwiązania definiują, jak projekty w rozwiązaniu mają być kompilowane i wdrażane. Konfiguracje projektu są zestawem właściwości projektu, które są unikatowe dla platformy i typu kompilacji (na przykład wydanie Win32). Można edytować domyślne konfiguracje oraz można tworzyć własne konfiguracje. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) i [NIB instrukcje: modyfikowanie właściwości projektu i ustawień konfiguracji](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 Spoza IDE można wykonywać następujące zadania dodatkowe:

- [Zmień katalog wyjściowy kompilacji](../ide/how-to-change-the-build-output-directory.md).

- [Zidentyfikuj projekty, które są zależne od danych wyjściowych z innego projektu w celu poprawnego skompilowania](../ide/how-to-create-and-remove-project-dependencies.md).

- [Zmień ilość informacji zawartych w dzienniku kompilacji lub oknie danych wyjściowych dla kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

- [Ukrywanie określonych ostrzeżeń kompilatora dla wizualizacji C#, C++wizualizacji lub Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

- [Określ niestandardowe akcje przed kompilacją i po kompilacji dla kompilacji](../ide/specifying-custom-build-events-in-visual-studio.md).

- Zwiększ wydajność kompilacji przy użyciu kompilacji równoległych. Aby uzyskać więcej informacji, zobacz [kompilowanie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) lub [Dostosowywanie C++ współbieżności kompilacji](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx)w blogu.

## <a name="see-also"></a>Zobacz też
 [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md) [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md) [zrozumienie platform kompilacji](../ide/understanding-build-platforms.md) [Kompilowanie (Kompilowanie) projekty witryny sieci Web](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [instrukcje: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md)
