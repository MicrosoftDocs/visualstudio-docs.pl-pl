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
# <a name="install-visual-studio-versions-side-by-side"></a>Instalowanie programu Visual Studio wersje Side-by-Side
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta wersja programu Visual Studio można zainstalować na komputerze, na którym jest już zainstalowana starsza wersja. Jeśli wystąpi błąd instalacji, możesz użyć [Narzędzia do zbierania dzienników](https://go.microsoft.com/fwlink/?LinkId=262077) do zbierania informacji o błędach, aby można było debugować problemy samodzielnie.

> [!NOTE]
> Zalecamy zainstalowanie wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w kolejności, w której zostały wydane. Na przykład należy zainstalować program Visual Studio 2013, przed zainstalowaniem programu Visual Studio 2015.

 Przed zainstalowaniem wersji obok siebie, przejrzyj następujące warunki:

- Jeśli używasz programu Visual Studio 2015 do otwierania rozwiązania, które zostało utworzone w [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], możesz później otworzyć i zmodyfikować rozwiązanie ponownie w starszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2015.

- Jeśli spróbujesz użyć programu Visual Studio 2015, aby otworzyć rozwiązanie, które zostało utworzone w [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] lub starszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2015. Aby uzyskać więcej informacji, zobacz stronę [port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) .

- W przypadku odinstalowania wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na komputerze, na którym jest zainstalowana więcej niż jedna wersja, skojarzenia plików dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostaną usunięte dla wszystkich wersji. Te skojarzenia plików można ponownie zamapować przy użyciu przycisku **Przywróć skojarzenia plików** na stronie **środowisko**, **Ogólne** okna dialogowego [Opcje](../ide/reference/general-environment-options-dialog-box.md) .

- Program Visual Studio nie aktualizuje automatycznie rozszerzeń, ponieważ nie wszystkie rozszerzenia są zgodne. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](https://go.microsoft.com/fwlink/?LinkId=178891) lub wydawcy oprogramowania.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Wersje programu .NET framework i instalacje Side-by-Side

- Projekty Visual Basic, C#wizualizacji i F# wizualizacji używają opcji **platformy docelowej** w **projektancie projektu** , aby określić, która wersja .NET Framework jest używana przez projekt. Dla projektu w języku C++ można ręcznie zmienić platformę docelową, modyfikując plik vcxproj. Aby uzyskać więcej informacji, zobacz [zgodność wersji](https://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Podczas tworzenia projektu można określić, która wersja .NET Framework obiektów docelowych projektu na liście **.NET Framework** w oknie dialogowym **Nowy projekt** .

     Aby uzyskać informacje specyficzne dla języka zobacz odpowiedni temat w poniższej tabeli.

    |Język|Temat|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[Konfigurowanie projektów](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[Instrukcje: modyfikowanie platformy docelowej i zestawu narzędzi platformy](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Uruchamianie aplikacji w języku JScript w poprzedniej wersji środowiska uruchomieniowego języka wspólnego](https://msdn.microsoft.com/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](../install/install-visual-studio-2015.md)
- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](https://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)