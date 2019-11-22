---
title: Instalowanie programu Visual Studio wersje Side-by-Side | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a146872561c4be5fe48016c17eb64ad6f854106a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298024"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalowanie obok siebie różnych wersji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta wersja programu Visual Studio można zainstalować na komputerze, na którym jest już zainstalowana starsza wersja. Jeśli wystąpi błąd instalacji, możesz użyć [narzędzie do zbierania dzienników](https://go.microsoft.com/fwlink/?LinkId=262077) do zbierania informacji o awarii, dzięki czemu użytkownik może samodzielnie zdebugować problemy.

> [!NOTE]
> Zaleca się zainstalowanie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wersje w kolejności, w której zostały wydane. Na przykład należy zainstalować program Visual Studio 2013, przed zainstalowaniem programu Visual Studio 2015.

 Przed zainstalowaniem wersji obok siebie, przejrzyj następujące warunki:

- Jeśli używasz programu Visual Studio 2015, aby otworzyć rozwiązanie utworzone w [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], można później otwierać i modyfikować rozwiązanie ponownie w starszej wersji, tak długo, jak jeszcze nie zaimplementowano żadnych funkcji, które są specyficzne dla programu Visual Studio 2015.

- Jeśli spróbujesz otworzyć rozwiązanie utworzone w przy użyciu programu Visual Studio 2015 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] lub starszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) strony.

- Jeśli odinstalujesz daną wersję programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na komputerze, który ma więcej niż jedna wersja zainstalowana, skojarzenia plików dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] są usuwane dla wszystkich wersji. Możesz ponownie zamapować te skojarzenia plików za pomocą **Przywróć skojarzenia plików** znajdujący się na **środowiska**, **ogólne** stronie [opcje](../ide/reference/general-environment-options-dialog-box.md) okno dialogowe.

- Program Visual Studio nie aktualizuje automatycznie rozszerzeń, ponieważ nie wszystkie rozszerzenia są zgodne. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](https://go.microsoft.com/fwlink/?LinkId=178891) lub od wydawcy oprogramowania.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Wersje programu .NET framework i instalacje Side-by-Side

- Visual Basic, Visual C#i Visual F# projektów użyj **platformę docelową** opcji **projektanta projektu** do określenia, która wersja programu .NET Framework projekt używa. Dla projektu w języku C++ można ręcznie zmienić platformę docelową, modyfikując plik vcxproj. Aby uzyskać więcej informacji, zobacz [zgodność wersji](https://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Podczas tworzenia projektu można określić, która wersja programu .NET Framework jest przeznaczony projekt **.NET Framework** listy w **nowy projekt** okno dialogowe.

     Aby uzyskać informacje specyficzne dla języka zobacz odpowiedni temat w poniższej tabeli.

    |Język|Temat|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[Konfigurowanie projektów](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[Instrukcje: modyfikowanie platformy docelowej i zestawu narzędzi platformy](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Uruchamianie aplikacji JScript w poprzedniej wersji środowiska uruchomieniowego języka wspólnego](https://msdn.microsoft.com/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md)
- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](https://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)