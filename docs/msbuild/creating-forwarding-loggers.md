---
title: Tworzenie rejestratorów przekazywania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 852b783129f130316de88580020e0139925ffb37
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634308"
---
# <a name="create-forwarding-loggers"></a>Tworzenie rejestratorów przekazywania

Rejestratory przekazywania zwiększają wydajność rejestrowania, umożliwiając wybranie zdarzeń, które mają być monitorowane podczas tworzenia projektów w systemie wieloprocesorowym. Włączając rejestratory przekazywania, można zapobiec niepożądanych zdarzeń z przytłaczające rejestratora centralnego, spowalniając czas kompilacji i zaśmiecania dziennika.

 Aby utworzyć rejestratora przekazywania, można zaimplementować <xref:Microsoft.Build.Framework.IForwardingLogger> interfejs, a następnie <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> zaimplementować jego metody ręcznie lub użyć klasy i jej wstępnie skonfigurowanych metod. (Ten ostatni wystarczy dla większości zastosowań.)

## <a name="register-events-and-respond-to-them"></a>Rejestrowanie zdarzeń i odpowiadanie na nie

 Rejestrator przekazywania zbiera informacje o zdarzeniach kompilacji, ponieważ są one zgłaszane przez aparat kompilacji pomocniczej, który jest procesem roboczym, który jest tworzony przez proces kompilacji głównej podczas kompilacji w systemie wieloprocesorowym. Następnie rejestrator przekazywania wybiera zdarzenia do przekazania do rejestratora centralnego, na podstawie instrukcji, które zostały mu podane.

 Należy zarejestrować rejestratory przekazywania do obsługi zdarzeń, które chcesz monitorować. Aby zarejestrować się dla zdarzeń, rejestratory należy zastąpić <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodę. Ta metoda zawiera teraz `nodecount`opcjonalny parametr , który można ustawić na liczbę procesorów w systemie. (Domyślnie wartość wynosi 1.)

 Przykładami zdarzeń, które <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>można <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>monitorować, są , i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

 W środowisku wieloprocesorowym komunikaty o zdarzeniach mogą być odbierane poza kolejnością. W związku z tym należy ocenić zdarzenia przy użyciu programu obsługi zdarzeń w rejestratorze przekazywania i zaprogramować go, aby określić, które zdarzenia przekazać do readresatora do przekazywania do rejestratora centralnego. Aby to osiągnąć, można <xref:Microsoft.Build.Framework.BuildEventContext> użyć klasy, która jest dołączona do każdej wiadomości, aby ułatwić identyfikowanie zdarzeń, które chcesz przekazać dalej, a następnie przekazać nazwy zdarzeń do <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasy (lub jej podklasy). Korzystając z tej metody, żadne inne specyficzne kodowanie jest wymagane do przekazywania zdarzeń.

## <a name="specify-a-forwarding-logger"></a>Określanie rejestratora przekazywania

 Po przekazywania rejestrator został skompilowany do zestawu, należy powiedzieć MSBuild używać go podczas kompilacji. Aby to zrobić, `-FileLogger` `-FileLoggerParameters`użyj `-DistributedFileLogger` , i przełączników wraz z *MSBuild.exe*. Przełącznik `-FileLogger` informuje *MSBuild.exe,* że rejestrator jest bezpośrednio dołączony. Przełącznik `-DistributedFileLogger` oznacza, że istnieje plik dziennika na węzeł. Aby ustawić parametry rejestratora przekazywania, `-FileLoggerParameters` użyj przełącznika. Aby uzyskać więcej informacji na temat tych i innych przełączników *MSBuild.exe,* zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Rejestratory obsługujące wiele procesorów

 Podczas tworzenia projektu w systemie wieloprocesorowym komunikaty kompilacji z każdego procesora nie są automatycznie przeplatane w ujednoliconej sekwencji. Zamiast tego należy ustanowić priorytet grupowania <xref:Microsoft.Build.Framework.BuildEventContext> wiadomości przy użyciu klasy, która jest dołączona do każdej wiadomości. Aby uzyskać więcej informacji na temat budowania wieloprocesorowego, zobacz [Rejestrowanie w środowisku wieloprocesorowym](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Tworzenie rejestratorów](../msbuild/build-loggers.md)
- [Logowanie w środowisku wieloprocesorowym](../msbuild/logging-in-a-multi-processor-environment.md)