---
title: Instalowanie wersji programu Visual Studio obok siebie | Microsoft Docs
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
ms.openlocfilehash: 1ef2d51e35a198dbe6da3c1a034dd7c8d1bf8922
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851022"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalowanie obok siebie różnych wersji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tę wersję programu Visual Studio można zainstalować na komputerze, na którym jest już zainstalowana wcześniejsza wersja. Jeśli wystąpi błąd instalacji, możesz użyć [Narzędzia do zbierania dzienników](https://www.microsoft.com/download/details.aspx?id=12493) do zbierania informacji o błędach, aby można było debugować problemy samodzielnie.

> [!NOTE]
> Zalecamy zainstalowanie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wersji w kolejności, w której zostały wydane. Na przykład zainstaluj Visual Studio 2013 przed zainstalowaniem programu Visual Studio 2015.

 Przed zainstalowaniem wersji obok siebie zapoznaj się z następującymi warunkami:

- Jeśli używasz programu Visual Studio 2015 do otwierania rozwiązania, które zostało utworzone w programie [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] , możesz później ponownie otworzyć i zmodyfikować rozwiązanie w starszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2015.

- Jeśli spróbujesz użyć programu Visual Studio 2015 do otwarcia rozwiązania, które zostało utworzone w programie [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] lub starszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2015. Aby uzyskać więcej informacji, zobacz stronę [port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) .

- W przypadku odinstalowania wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na komputerze, na którym jest zainstalowana więcej niż jedna wersja, skojarzenia plików dla programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostaną usunięte dla wszystkich wersji. Te skojarzenia plików można ponownie zamapować przy użyciu przycisku **Przywróć skojarzenia plików** na stronie **środowisko**, **Ogólne** okna dialogowego [Opcje](../ide/reference/general-environment-options-dialog-box.md) .

- Program Visual Studio nie uaktualnia automatycznie rozszerzeń, ponieważ nie wszystkie rozszerzenia są zgodne. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](https://visualstudiogallery.msdn.microsoft.com/) lub wydawcy oprogramowania.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Wersje .NET Framework i instalacje równoczesne

- Visual Basic, Visual C# i projekty Visual F# używają opcji **platformy docelowej** w **projektancie projektu** , aby określić, która wersja .NET Framework jest używana przez projekt. W przypadku projektu języka C++ można ręcznie zmienić platformę docelową, modyfikując plik. vcxproj. Aby uzyskać więcej informacji, zobacz [zgodność wersji](https://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Podczas tworzenia projektu można określić, która wersja .NET Framework obiektów docelowych projektu na liście **.NET Framework** w oknie dialogowym **Nowy projekt** .

     Aby uzyskać informacje dotyczące języka, zobacz odpowiedni temat w poniższej tabeli.

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
- [Kompilowanie aplikacji izolowanych C/C++ i zestawów równoległych](https://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)
