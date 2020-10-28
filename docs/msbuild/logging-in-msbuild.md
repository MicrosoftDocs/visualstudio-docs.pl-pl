---
title: Logowanie w programie MSBuild | Microsoft Docs
description: Dowiedz się, w jaki sposób rejestrowanie MSBuild umożliwia monitorowanie postępów kompilacji przez przechwytywanie zdarzeń kompilacji, komunikatów, ostrzeżeń i błędów w pliku dziennika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9de830003571f1f648cf06be634d9a773b95269f
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904338"
---
# <a name="logging-in-msbuild"></a>Logowanie w programie MSBuild

Rejestrowanie zapewnia sposób monitorowania postępu kompilacji. Rejestrowanie przechwytuje zdarzenia kompilacji, komunikaty, ostrzeżenia i błędy w pliku dziennika.

## <a name="in-this-section"></a>W tej sekcji

- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

 Opisuje różne aspekty rejestrowania w programie MSBuild.

- [Rejestratory kompilacji](../msbuild/build-loggers.md)

 Przedstawia kroki wymagane do utworzenia jednoprocesorowego rejestratora.

- [Rejestrowanie w środowisku wieloprocesorowym](../msbuild/logging-in-a-multi-processor-environment.md)

 Opisuje sposób rejestrowania działa w środowisku wieloprocesorowym i dwóch modelach rejestrowania z obsługą wiele procesorów.

- [Zapisuj rejestratory obsługujące wiele procesorów](../msbuild/writing-multi-processor-aware-loggers.md)

 Przedstawia sposób tworzenia rejestratorów obsługujących wiele procesorów i korzystania z ConfigurableForwardingLogger.

- [Utwórz rejestratory przekazywania](../msbuild/creating-forwarding-loggers.md)

 Zawiera instrukcje tworzenia niestandardowych rejestratorów przesyłania dalej.

## <a name="see-also"></a>Zobacz także

- [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) Opisuje sposób szybszego kompilowania wielu projektów przez uruchamianie ich równolegle.
