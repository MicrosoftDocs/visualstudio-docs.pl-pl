---
title: Zarządzanie zasobami aplikacji (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efe2b176db9f6f22f9e38775d5fc8acad87655ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651385"
---
# <a name="managing-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki zasobów są plikami, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub pliki audio. Ponieważ te pliki nie są częścią procesu kompilacji, można je zmienić bez konieczności ponownego kompilowania plików binarnych. Jeśli planujesz lokalizowanie aplikacji, należy używać plików zasobów dla wszystkich ciągów i innych zasobów, które należy zmienić podczas lokalizowania aplikacji.

 Aby uzyskać więcej informacji o zasobach w aplikacjach klasycznych platformy .NET, zobacz [zasoby w aplikacjach klasycznych](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). Aby uzyskać więcej informacji o zasobach w C++ aplikacjach klasycznych, zobacz [Praca z plikami zasobów](https://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).

 Aplikacje ze sklepu Windows używają różnych modeli zasobów z aplikacji klasycznych. Aby uzyskać informacje o zasobach w aplikacji do sklepu Windows, zobacz [Definiowanie zasobów aplikacji](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) w witrynie sieci Web Centrum deweloperów systemu Windows.

## <a name="working-with-resources"></a>Praca z zasobami
 W projekcie kodu zarządzanego Otwórz okno właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz **Właściwości**lub wpisz **właściwości projektu** w oknie **Szybkie uruchamianie** lub wpisz Alt + Enter w  **Okno Eksplorator rozwiązań** ). Wybierz kartę **zasoby** . Plik. resx można dodać, jeśli projekt nie zawiera już jednego z nich, dodawać i usuwać różne rodzaje zasobów oraz modyfikować istniejące zasoby.

 Aby dowiedzieć się, jak korzystać z zasobów C++ w projektach, zobacz [How to: Create a Resource](https://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716).
