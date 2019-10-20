---
title: Weryfikacja systemu w czasie opracowywania
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 328b600a21adf274d1d016f595438eb5622ee853
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663735"
---
# <a name="validate-your-system-during-development"></a>Weryfikacja systemu w czasie opracowywania

Program Visual Studio może pomóc zapewnić spójność oprogramowania z wymaganiami użytkowników i architekturą systemu.

Aby sprawdzić, które wersje programu Visual Studio obsługują każdą z tych funkcji, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Najważniejsze zadania

Aby sprawdzić poprawność oprogramowania, wykonaj następujące zadania:

|**Zadania**|**Skojarzone tematy**|
|-|-|
|Upewnij **się, że oprogramowanie spełnia wymagania użytkowników**:<br /><br />Używaj wymagań i modeli architektonicznych, aby pomóc w organizowaniu testów systemu i jego składników. Dzięki temu można sprawdzić wymagania, które są ważne dla użytkowników i innych uczestników projektu, oraz ułatwić szybkie aktualizowanie testów w przypadku zmiany wymagań.|- [opracowywanie testów z modelu](../modeling/develop-tests-from-a-model.md)|
|**Upewnij się, że oprogramowanie pozostaje spójne z zamierzonym projektem systemu:**<br /><br />Diagramy zależności opisują zamierzone zależności między składnikami aplikacji. Podczas opracowywania można sprawdzić, czy rzeczywiste zależności w kodzie są zgodne z zamierzonym projektem.|- [utworzyć diagramy zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [sprawdzać poprawność kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategorii**|**Linki**|
|-|-|
|**Filmy wideo**|![link wideo ](../data-tools/media/playvideo.gif) [kanału 9: Doug siedem: zrozumienie kodu i projektowanie systemów za pomocą programu Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![link wideo ](../data-tools/media/playvideo.gif) [kanału 9: projektowanie aplikacji](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Dotyczące**|- [Wizualizacja programu Visual Studio & narzędzia do modelowania](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [rozszerzalności programu Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Zobacz także

- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
