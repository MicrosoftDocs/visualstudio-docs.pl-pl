---
title: Weryfikacja systemu w czasie opracowywania
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fb9810f1c212dfb881f5725676a79c6307b9cfa
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476504"
---
# <a name="validate-your-system-during-development"></a>Weryfikacja systemu w czasie opracowywania

Visual Studio może pomóc zachować oprogramowania zgodne z wymaganiami użytkownika oraz o architekturze systemu.

Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdą z tych funkcji, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Kluczowe zadania

Aby zweryfikować swoje oprogramowanie, należy wykonać poniższe zadania:

|**Zadania**|**Skojarzone tematy**|
|-|-|
|**Upewnij się, oprogramowaniu spełnia wymagania użytkowników**:<br /><br />Aby ułatwić organizowanie testów systemu i jego składników, należy użyć wymagań i architektury modeli. Praktyka ta pomaga zagwarantować, że testowania wymagań które są ważne dla użytkowników i innych zainteresowanych stron i pomaga szybko aktualizować testów, gdy zmienią się wymagania.|- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)|
|**Upewnij się, że oprogramowanie pozostanie spójna z zamierzonego projektu systemu:**<br /><br />Diagramy zależności opisywanie zakładanych zależności między składnikami aplikacji. Podczas tworzenia aplikacji można sprawdzić, że rzeczywiste zależności w kodzie są zgodne z zamierzonego projektu.|- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Łącza**|
|-|-|
|**Filmy wideo**|![Link do klipu wideo](../data-tools/media/playvideo.gif) [witryny Channel 9: Doug Seven: Rozpoznawanie kodu oraz projektowanie systemów za pomocą programu Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![Link do klipu wideo](../data-tools/media/playvideo.gif) [witryny Channel 9: Projektowanie aplikacji](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Fora**|- [Program Visual Studio visualization and Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Rozszerzeń programu Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Zobacz także

- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
