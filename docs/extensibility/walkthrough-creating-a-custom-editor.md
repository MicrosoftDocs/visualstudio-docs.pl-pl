---
title: 'Przewodnik: Tworzenie edytora niestandardowego | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697672"
---
# <a name="walkthrough-create-a-custom-editor"></a>Przewodnik: Tworzenie edytora niestandardowego
Szablon projektu VSPackage można utworzyć prosty edytor niestandardowy w języku C++. Szablon projektu VSPackage nie obsługuje już projektów języka C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Szablon projektu pakietu programu Visual Studio
 Szablon projektu pakietu programu Visual Studio można znaleźć w oknie dialogowym **Nowy projekt** w folderze **Rozszerzalność języka C++.**

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Aby utworzyć pakiet VSPackage przy użyciu szablonu pakietu programu Visual Studio

1. Utwórz projekt za pomocą szablonu pakietu programu Visual Studio.

2. Wybierz opcję **Edytor niestandardowy** i kliknij przycisk **Dalej**. Zostanie **wyświetlona** strona Opcje edytora.

3. Wpisz nazwę edytora w polu **Nazwa edytora.** Wpisz rozszerzenie pliku, które ma być skojarzone z edytorem, w polu **Rozszerzenie pliku.** Edytor jest dostępny dla plików z tym rozszerzeniem. Rozszerzenie pliku jest zarejestrowane tylko dla programu Visual Studio, a nie dla systemu Windows. Wpisz domyślną nazwę pliku dla nowych dokumentów utworzonych za pomocą edytora w polu **Domyślna nazwa pliku.**

4. Kliknij **przycisk Zakończ,** aby utworzyć pakiet VSPackage w folderze określonym.

### <a name="to-test-your-custom-editor"></a>Aby przetestować edytor niestandardowy

1. W menu **Plik** wskaż polecenie **Nowy,** a następnie kliknij polecenie **Plik**.

2. W okienku **Zainstalowane szablony** okna dialogowego **Nowy plik** wybierz szablon pliku, a następnie zarejestrowany typ pliku.

3. Kliknij **przycisk Otwórz,** aby wyświetlić i edytować dokument.

     Edytor obsługuje operacje wycinania i wklejania, znajdowania i zamieniania oraz operacji otwierania i ładowania.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
