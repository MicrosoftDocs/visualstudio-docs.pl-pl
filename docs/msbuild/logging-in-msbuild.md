---
title: Logowanie w programie MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99bbb6ba880ace8b21ae6b6009ee84cffee79485
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856033"
---
# <a name="logging-in-msbuild"></a>Logowanie w programie MSBuild
Rejestrowanie umożliwia możesz monitorować postępy kompilacji. Przechwytywanie rejestrowanie kompilacji, zdarzenia, komunikaty, ostrzeżenia i błędy w pliku dziennika.

## <a name="in-this-section"></a>W tej sekcji
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

 W tym artykule opisano różne aspekty logowania [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

- [Rejestratory kompilacji](../msbuild/build-loggers.md)

 Omówiono kroki wymagane do utworzenia rejestratora jednoprocesorowym.

- [Logowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md)

 W tym artykule opisano, jak działa logowanie w środowisku wielu procesorów i dwa modele rejestrowanie wielu procesorów.

- [Zapis procesorów uwzględniających rejestratorów](../msbuild/writing-multi-processor-aware-loggers.md)

 Opisano sposób tworzenia wielu procesorów rejestratorów uwzględniających wiele oraz jak używać ConfigurableForwardingLogger.

- [Tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md)

 Zawiera opis sposobu tworzenia niestandardowych przekazywanie rejestratorów.

## <a name="see-also"></a>Zobacz także
- [Tworzenie wielu projektów w sposób równoległy](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) w tym artykule opisano sposób tworzenia wielu projektów przez uruchomienie ich równolegle.