---
title: 'Przewodnik: Tworzenie edytora niestandardowego | Microsoft Docs'
description: Dowiedz się, jak szablon projektu pakietu VSPackage może utworzyć prosty edytor niestandardowy w języku C++ za pomocą tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a4ebcf99634012943ed0a7fd1a72b5d4852729e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931386"
---
# <a name="walkthrough-create-a-custom-editor"></a>Przewodnik: Tworzenie edytora niestandardowego
Szablon projektu pakietu VSPackage może utworzyć prosty edytor niestandardowy w języku C++. Szablon projektu pakietu VSPackage nie obsługuje już projektów C# ani Visual Basic. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Szablon projektu pakietu programu Visual Studio
 Szablon projektu pakietu programu Visual Studio można znaleźć w oknie dialogowym **Nowy projekt** w obszarze folder **rozszerzalności języka C++** .

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Aby utworzyć pakietu VSPackage przy użyciu szablonu pakietu programu Visual Studio

1. Utwórz projekt z szablonem pakietu programu Visual Studio.

2. Wybierz opcję **Edytor niestandardowy** , a następnie kliknij przycisk **dalej**. Zostanie wyświetlona strona **Opcje edytora** .

3. W polu **Nazwa edytora** wpisz nazwę edytora. Wpisz rozszerzenie pliku, które ma być skojarzone z edytorem w polu **rozszerzenie pliku** . Edytor jest dostępny dla plików z tym rozszerzeniem. Rozszerzenie pliku jest zarejestrowane wyłącznie dla programu Visual Studio, a nie dla systemu Windows. W polu **Domyślna nazwa pliku** wpisz domyślną nazwę pliku dla nowych dokumentów utworzonych za pomocą edytora.

4. Kliknij przycisk **Zakończ** , aby utworzyć pakietu VSPackage w określonym folderze.

### <a name="to-test-your-custom-editor"></a>Aby przetestować Edytor niestandardowy

1. W menu **plik** wskaż polecenie **Nowy** , a następnie kliknij polecenie **plik**.

2. W okienku **zainstalowane szablony** okna dialogowego **nowy plik** wybierz szablon pliku, a następnie zarejestrowany typ pliku.

3. Kliknij przycisk **Otwórz** , aby wyświetlić i edytować dokument.

     Edytor obsługuje operacje wycinania i wklejania, znajdowania i zastępowania oraz otwierania i ładowania.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
