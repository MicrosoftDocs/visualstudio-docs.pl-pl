---
title: Kompilowanie i tworzenie
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3d94289baf5cd7b3e4724f205dbfcb5e0ff227eb
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "53931067"
---
# <a name="compiling-and-building-in-visual-studio"></a>Kompilowanie i tworzenie w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można używać programu Visual Studio do kompilacji aplikacji i do tworzenia zestawów oraz programów wykonywalnych w krótkich odstępach czasu podczas cyklu rozwoju. Dzięki częstym kompilacjom kodu, można wcześniej wykryć błędy czasu kompilacji, takie jak niepoprawna składnia, błędnie napisane słowa kluczowe i niezgodności typów. Można także wykryć i poprawić błędy czasu wykonania, takie jak błędy logiczne i semantyczne, dzięki częstym kompilacjom i uruchamianiu wersji debugowania kodu.

 Kiedy projekt lub rozwiązanie jest już w pełni rozwinięte i zdebugowane, można skompilować jego składniki poprzez kompilację wydania. Domyślnie kompilacja wydania jest zoptymalizowana i zaprojektowana, aby była mniejsza i działała szybciej niż wersja do debugowania. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Wybieranie metody kompilacji
 Aplikację można skompilować za pomocą domyślnych opcji kompilacji w IDE, w wierszu polecenia lub przy użyciu Team Foundation Build. Każda z tych opcji używa programu MSBuild jako podstawowej technologii, a każde podejście ma określone korzyści, jak pokazano w poniższej tabeli.

|Metoda kompilacji|Zalety|Więcej informacji|
|------------------|--------------|--------------------------|
|Używanie IDE|-Można łatwiej tworzyć i natychmiast uruchamiać kompilacje.<br />— Można uruchomić kompilację na wielu procesorach dla projektów C++ i C#.<br />— Można dostosować niektóre aspekty systemu kompilacji.|[Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|Uruchomienie wiersza polecenia MSBuild|— Można kompilować projekty bez konieczności instalowania programu Visual Studio.<br />— Można uruchomić kompilację na wielu procesorach dla wszystkich typów projektów.<br />— Można dostosować większość obszarów systemu kompilacji.|[MSBuild](../msbuild/msbuild.md)|
|Użycie Team Foundation Build|— Można zautomatyzować proces kompilacji. Można na przykład skompilować jeden lub więcej projektów w nocy lub za każdym razem, kiedy kod jest zaewidencjonowany. Można również kompilować projekty na udostępnionych serwerach kompilacji, a nie na komputerze dewelopera.<br />— Można szybko określić kod, który ma być skompilowany, testy, które chcesz uruchomić, oraz inne typowe opcje.<br />— Można modyfikować przepływ kompilacji, a w razie potrzeby, tworzyć aktywności kompilacji, aby wykonywać zadania wysoce niestandardowe.|[Kompiluj aplikację](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|

## <a name="building-from-the-ide"></a>Kompilacja z IDE
 Podczas tworzenia projektu domyślne konfiguracje kompilacji zostają dla niego zdefiniowane, a konfiguracja kompilacji rozwiązania zostaje do niego przypisana, aby dostarczyć kontekst dla kompilacji. Konfiguracje rozwiązania definiują, jak projekty w rozwiązaniu mają być kompilowane i wdrażane. Konfiguracje projektu są zestawem właściwości projektu, które są unikatowe dla platformy i typu kompilacji (na przykład wydanie Win32). Można edytować domyślne konfiguracje oraz można tworzyć własne konfiguracje. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7) i [NIB jak: Modyfikowanie właściwości projektu i ustawień konfiguracji](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 Spoza IDE można wykonywać następujące zadania dodatkowe:

-   [Zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md).

-   [Identyfikuj projekty, które są zależne od danych wyjściowych z innego projektu w celu poprawnej kompilacji](../ide/how-to-create-and-remove-project-dependencies.md).

-   [Zmień ilość informacji zawartych w dzienniku kompilacji lub okno danych wyjściowych kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

-   [Ukryj określone ostrzeżenia kompilatora Visual C#, Visual C++ lub Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

-   [Określ niestandardowe przed kompilacją i po zakończeniu kompilowania akcje w przypadku kompilacji](../ide/specifying-custom-build-events-in-visual-studio.md).

-   Zwiększ wydajność kompilacji przy użyciu kompilacji równoległych. Aby uzyskać więcej informacji, zobacz [tworzenie wielu projektów w sposób równoległy](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) lub wpis w blogu [dostrajanie kompilacji równoległych C++](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx).

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md) [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md) [interpretacji platformy kompilacji](../ide/understanding-build-platforms.md) [tworzenia projektów witryny sieci Web (kompilowanie)](http://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [ Jak: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md)
