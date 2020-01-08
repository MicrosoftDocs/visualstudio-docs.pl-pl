---
title: Logowanie w programie MSBuild | Microsoft Docs
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
ms.openlocfilehash: 24a769f6d0b9aa847899c02c951921dc77bac21a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592194"
---
# <a name="logging-in-msbuild"></a>Logowanie w programie MSBuild
Rejestrowanie zapewnia sposób monitorowania postępu kompilacji. Rejestrowanie przechwytuje zdarzenia kompilacji, komunikaty, ostrzeżenia i błędy w pliku dziennika.

## <a name="in-this-section"></a>W tej sekcji
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

 Opisuje różne aspekty rejestrowania w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

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
