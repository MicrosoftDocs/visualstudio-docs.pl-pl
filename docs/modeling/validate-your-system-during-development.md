---
title: Weryfikacja systemu w czasie opracowywania
description: Dowiedz się Visual Studio pomaga zachować spójność oprogramowania z wymaganiami użytkownika i architekturą systemu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae85c7f98aab3e852a810976cc1cecbd83b65307
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388376"
---
# <a name="validate-your-system-during-development"></a>Weryfikacja systemu w czasie opracowywania

Visual Studio zachować spójność oprogramowania z wymaganiami użytkownika i architekturą systemu.

Aby sprawdzić, które wersje Visual Studio obsługują każdą z tych funkcji, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="key-tasks"></a>Kluczowe zadania

Aby zweryfikować oprogramowanie, należy wykonywać następujące zadania:

|**Zadania**|**Skojarzone tematy**|
|-|-|
|**Upewnij się, że oprogramowanie spełnia wymagania użytkowników:**<br /><br />Wymagania i modele architektoniczne ułatwiają organizowanie testów systemu i jego składników. Takie rozwiązanie pomaga w przetestowaniu wymagań, które są ważne dla użytkowników i innych uczestników projektu, oraz pomaga szybko aktualizować testy po zmianie wymagań.|- [Opracowywanie testów z modelu](../modeling/develop-tests-from-a-model.md)|
|**Upewnij się, że oprogramowanie pozostaje zgodne z zamierzony projekt systemu:**<br /><br />Diagramy zależności opisują zamierzone zależności między składnikami aplikacji. Podczas opracowywania można sprawdzić, czy rzeczywiste zależności w kodzie są zgodne z zamierzony projekt.|- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Weryfikowanie kodu za pomocą diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|-|-|
|**Filmy wideo**|![link do filmu wideo ](../data-tools/media/playvideo.gif) [Channel 9: Doug Seven: Code Understanding and Systems Design with Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![link do filmu wideo ](../data-tools/media/playvideo.gif) [Channel 9: Architecting an Application (Channel 9: Architecting an Application )](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application)|
|**Fora**|- [Visual Studio Visualization & Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio rozszerzalność](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Zobacz też

- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
