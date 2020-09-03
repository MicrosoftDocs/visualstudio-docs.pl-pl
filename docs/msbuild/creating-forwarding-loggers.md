---
title: Tworzenie rejestratorów przekazywania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634308"
---
# <a name="create-forwarding-loggers"></a>Utwórz rejestratory przekazywania

Rejestratory przesyłania dalej zwiększają efektywność rejestrowania, umożliwiając wybranie zdarzeń, które mają być monitorowane podczas kompilowania projektów w systemie wieloprocesorowym. Włączając rejestratory przesyłania dalej, można zapobiegać niepożądanym zdarzeniom w celu przeciążania centralnego rejestratora, spowalniać czas kompilacji i zaśmiecać dziennik.

 Aby utworzyć rejestratora przekazywania, można zaimplementować <xref:Microsoft.Build.Framework.IForwardingLogger> interfejs, a następnie wdrożyć jego metody ręcznie lub użyć <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasy i jej wstępnie skonfigurowanych metod. (Ostatnie będzie wystarczające dla większości aplikacji).

## <a name="register-events-and-respond-to-them"></a>Rejestrowanie zdarzeń i reagowanie na nie

 Rejestrator przekazywania zbiera informacje o zdarzeniach kompilacji, które są zgłaszane przez pomocniczy aparat kompilacji, który jest procesem roboczym tworzonym przez główny proces kompilacji podczas kompilacji w systemie wieloprocesorowym. Następnie Rejestrator przekazywania wybiera zdarzenia do przekazywania do centralnego rejestratora na podstawie instrukcji, które zostały przez Ciebie podane.

 Należy zarejestrować rejestratory przekazywania, aby obsługiwać zdarzenia, które mają być monitorowane. Aby zarejestrować zdarzenia, rejestratory muszą przesłaniać <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodę. Ta metoda zawiera teraz opcjonalny parametr, `nodecount` który może być ustawiony na liczbę procesorów w systemie. (Domyślnie wartość wynosi 1).

 Przykłady zdarzeń, które można monitorować, to, <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> .

 W środowisku wieloprocesorowym komunikaty o zdarzeniach mogą być odbierane poza kolejnością. W związku z tym należy oszacować zdarzenia przy użyciu programu obsługi zdarzeń w rejestratorze przekazywania i programować go w celu określenia zdarzeń, które mają zostać przekazane do readresatora w celu przekazywania do centralnego rejestratora. Aby to osiągnąć, można użyć <xref:Microsoft.Build.Framework.BuildEventContext> klasy, która jest dołączona do każdego komunikatu, aby pomóc identyfikować zdarzenia, które chcesz przekazywać, a następnie przekazać nazwy zdarzeń do <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasy (lub podklasy IT). W przypadku korzystania z tej metody do przesyłania dalej zdarzeń nie jest wymagane żadne inne kodowanie.

## <a name="specify-a-forwarding-logger"></a>Określ Rejestrator przekazujący

 Po skompilowaniu rejestratora przekazywania do zestawu, należy poinformować program MSBuild, aby używał go podczas kompilacji. W tym celu należy użyć `-FileLogger` parametrów, `-FileLoggerParameters` , i `-DistributedFileLogger` razem z *MSBuild.exe*. `-FileLogger`Przełącznik informuje *MSBuild.exe* , że Rejestrator jest bezpośrednio dołączony. `-DistributedFileLogger`Przełącznik oznacza, że istnieje plik dziennika na węzeł. Aby ustawić parametry dla rejestratora przekazywania, użyj `-FileLoggerParameters` przełącznika. Aby uzyskać więcej informacji na temat tych i innych przełączników *MSBuild.exe* , zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Rejestratory obsługujące wiele procesorów

 Podczas kompilowania projektu w systemie wieloprocesorowym komunikaty kompilacji z poszczególnych procesorów nie są automatycznie przeplatane w ujednoliconej sekwencji. Zamiast tego należy określić priorytet grupowania komunikatów przy użyciu <xref:Microsoft.Build.Framework.BuildEventContext> klasy dołączonej do każdej wiadomości. Aby uzyskać więcej informacji na temat tworzenia wielu procesorów, zobacz [Rejestrowanie w środowisku wieloprocesorowym](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Rejestratory kompilacji](../msbuild/build-loggers.md)
- [Rejestrowanie w środowisku wieloprocesorowym](../msbuild/logging-in-a-multi-processor-environment.md)