---
title: 'Przewodnik: Tworzenie niestandardowego edytora | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b1b4e59e43a4a5aeb129464a34b96ef3f665e72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148872"
---
# <a name="walkthrough-creating-a-custom-editor"></a>Przewodnik: Tworzenie edytora niestandardowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon projektu pakietu VSPackage można utworzyć proste edytora niestandardowego w języku C++.  Szablon projektu pakietu VSPackage już nie obsługuje projektów C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Szablon projektu pakietu Visual Studio  
 Szablon projektu pakietu Visual Studio można znaleźć w **nowy projekt** okna dialogowego z folderu rozszerzeń języka C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Do utworzenia pakietu VSPackage przy użyciu szablonu pakiet rozszerzeń Visual Studio  
  
1. Utwórz projekt za pomocą szablonu pakietu Visual Studio.  
  
2. Wybierz **edytora niestandardowego** opcji, a następnie kliknij przycisk **dalej**. **Opcji edytora** zostanie wyświetlona strona.  
  
3. Wpisz nazwę w edytorze **nazwa edytora** pole. Wpisz rozszerzenie pliku, który ma zostać skojarzony z edytora w **rozszerzenie pliku** pole. Edytor jest dostępna dla plików za pomocą tego rozszerzenia. Rozszerzenie pliku jest zarejestrowane dla programu Visual Studio, nie dla Windows. Wpisz nazwę pliku domyślne dla nowych dokumentów utworzonych za pomocą edytora w **domyślnej nazwy pliku** pole.  
  
4. Kliknij przycisk **Zakończ** do utworzenia Twojego pakietu VSPackage w podanym folderze.  
  
### <a name="to-test-your-custom-editor"></a>Aby przetestować niestandardowego edytora  
  
1. Na **pliku** menu wskaż **New** a następnie kliknij przycisk **pliku**.  
  
2. W **zainstalowane szablony** okienku **nowy plik** okno dialogowe, wybierz szablon pliku, a następnie plik typ właśnie zostało zarejestrowane.  
  
3. Kliknij przycisk **Otwórz** do wyświetlania i edytowania dokumentu.  
  
     Edytor obsługuje operacje kopiowania i wklejania, Znajdź i Zamień i open i obciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
