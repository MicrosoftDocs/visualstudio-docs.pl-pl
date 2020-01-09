---
title: Weryfikacja systemu w czasie opracowywania
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae2b7d81b1f166e6cc97debc3291661d59ee6960
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594035"
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

|**Kategoria**|**Linki**|
|-|-|
|**Filmy wideo**|![link do wideo](../data-tools/media/playvideo.gif) [kanału 9: Doug siedem: zrozumienie kodu i projektowanie systemów za pomocą programu Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![link do wideo](../data-tools/media/playvideo.gif) [kanału 9: projektowanie aplikacji](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Fora**|- [Wizualizacja programu Visual Studio & narzędzia do modelowania](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [rozszerzalności programu Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Zobacz także

- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
