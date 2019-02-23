---
title: 'Przewodnik: Tworzenie niestandardowego edytora | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90c6456789762943422384755212edef1456a499
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705388"
---
# <a name="walkthrough-create-a-custom-editor"></a>Przewodnik: Tworzenie edytora niestandardowego
Szablon projektu pakietu VSPackage można utworzyć proste edytora niestandardowego w języku C++. Szablon projektu pakietu VSPackage już nie obsługuje projektów C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Szablon projektu pakietu Visual Studio
 Można znaleźć szablonu projektu pakietu Visual Studio w **nowy projekt** , okno dialogowe **rozszerzalności C++** folderu.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Do utworzenia pakietu VSPackage przy użyciu szablonu pakietu Visual Studio

1.  Utwórz projekt za pomocą szablonu pakietu Visual Studio.

2.  Wybierz **edytora niestandardowego** opcji, a następnie kliknij przycisk **dalej**. **Opcji edytora** zostanie wyświetlona strona.

3.  Wpisz nazwę w edytorze **nazwa edytora** pole. Wpisz rozszerzenie pliku, który ma zostać skojarzony z edytora w **rozszerzenie pliku** pole. Edytor jest dostępna dla plików za pomocą tego rozszerzenia. Rozszerzenie pliku jest zarejestrowane dla programu Visual Studio, nie dla Windows. Wpisz nazwę pliku domyślne dla nowych dokumentów utworzonych za pomocą edytora w **domyślnej nazwy pliku** pole.

4.  Kliknij przycisk **Zakończ** do utworzenia Twojego pakietu VSPackage w podanym folderze.

### <a name="to-test-your-custom-editor"></a>Aby przetestować niestandardowego edytora

1.  Na **pliku** menu wskaż **New** a następnie kliknij przycisk **pliku**.

2.  W **zainstalowane szablony** okienku **nowy plik** okno dialogowe, wybierz szablon pliku, a następnie plik typ zarejestrowany.

3.  Kliknij przycisk **Otwórz** do wyświetlania i edytowania dokumentu.

     Edytor obsługuje operacje kopiowania i wklejania, Znajdź i Zamień i open i obciążenia.

## <a name="see-also"></a>Zobacz także
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)