---
title: Zarządzanie zasobami aplikacji (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1681484500c382b296a03e78661b808825768a5b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58789150"
---
# <a name="manage-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)

Pliki zasobów są pliki, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub pliki audio. Ponieważ te pliki nie są częścią procesu kompilacji, można je zmienić, bez konieczności ponownego kompilowania plików binarnych. Jeśli planowane jest zlokalizować aplikację, należy użyć plików zasobów dla wszystkich ciągów i innych zasobów, które muszą zostać zmienione podczas lokalizowania aplikacji.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources).

Aby uzyskać więcej informacji na temat zasobów w aplikacjach klasycznych .NET, zobacz [zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Praca z zasobami

W projekcie kodu zarządzanego Otwórz okno właściwości projektu. W oknie właściwości można otworzyć przez:

- Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierając polecenie **właściwości**
- Wpisywanie **właściwości projektu** w **Ctrl**+**Q** pole wyszukiwania
- Wybieranie **Alt**+**wprowadź** w **Eksploratora rozwiązań**

Wybierz **zasobów** kartę. Możesz dodać *resx* plik, jeśli projekt nie zawiera jeden już, dodawanie i usuwanie różnych rodzajów zasobów i zmodyfikowania istniejących zasobów.

## <a name="resources-in-other-project-types"></a>Zasoby w innych typów projektów

Zasoby są zarządzane w różny sposób w projektach platformy .NET niż w innych typów projektów. Aby uzyskać więcej informacji na temat zasobów:

- Aplikacje uniwersalne platformy Windows (UWP), zobacz [zasobów aplikacji i systemu zarządzania zasobów](/windows/uwp/app-resources/)
- Projekty języka C++, zobacz [pracy z plikami zasobów](/cpp/windows/working-with-resource-files) i [jak: Utwórz zasób](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Zobacz także

- [Zasoby w aplikacjach komputerowych (.NET Framework)](/dotnet/framework/resources/index)
- [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources)
