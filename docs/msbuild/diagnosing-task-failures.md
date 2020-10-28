---
title: Diagnozowanie błędów zadań | Microsoft Docs
description: Dowiedz się, jak zdiagnozować błędy zadań programu MSBuild, identyfikując zadanie zakończone niepowodzeniem, nazwę narzędzia i inne informacje.
ms.custom: SEO-VS-2020
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaf55cc529be8fc61e05d1a76096e26d965aa136
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796475"
---
# <a name="diagnosing-task-failures"></a>Diagnozowanie błędów zadań

`MSB6006` jest emitowany, gdy <xref:Microsoft.Build.Utilities.ToolTask> Klasa pochodna uruchamia proces narzędzia, który zwraca niezerowy kod zakończenia, jeśli zadanie nie zarejestrował bardziej szczegółowego błędu.

## <a name="identifying-the-failing-task"></a>Identyfikowanie zadania, które kończy się niepowodzeniem

Gdy napotkasz błąd zadania, pierwszym krokiem jest zidentyfikowanie zadania, które kończy się niepowodzeniem.

Tekst błędu określa nazwę narzędzia (przyjazną nazwę dostarczoną przez implementację zadania <xref:Microsoft.Build.Utilities.ToolTask.ToolName> lub nazwę pliku wykonywalnego) i liczbowy kod zakończenia. Na przykład w przeglądarce

```text
error MSB6006: "custom tool" exited with code 1.
```

Nazwa narzędzia to `custom tool` i kod zakończenia `1` .

### <a name="command-line-builds"></a>Kompilacje w wierszu polecenia

Jeśli kompilacja została skonfigurowana w taki sposób, aby zawierała Podsumowanie (wartość domyślna), podsumowanie będzie wyglądać następująco:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Ten wynik wskazuje, że błąd wystąpił w zadaniu zdefiniowanym w wierszu 19 pliku `S:\MSB6006_demo\MSB6006_demo.csproj` w obiekcie docelowym o nazwie `InvokeToolTask` w projekcie `S:\MSB6006_demo\MSB6006_demo.csproj` .

### <a name="in-visual-studio"></a>W programie Visual Studio

Te same informacje są dostępne na liście błędów programu Visual Studio w kolumnach `Project` , `File` i `Line` .

## <a name="finding-more-failure-information"></a>Znajdowanie dalszych informacji o niepowodzeniu

Ten błąd jest emitowany, gdy zadanie nie zarejestrował konkretnego błędu. Niepowodzenie rejestrowania błędu jest często spowodowane tym, że zadanie nie jest skonfigurowane do zrozumienia formatu błędu emitowanego przez to narzędzie.

Dobrze działające narzędzia zwykle emitują pewne informacje kontekstowe lub błędy do ich standardowego wyjścia lub strumienia błędów, a także domyślnie przechwytują i rejestrują te informacje. Poszukaj wpisów dziennika przed wystąpieniem błędu, aby uzyskać dodatkowe informacje. Aby zachować te informacje, może być konieczne ponowne uruchomienie kompilacji z wyższym poziomem dziennika.

## <a name="next-steps"></a>Następne kroki

Miejmy nadzieję, dodatkowy kontekst lub błędy zidentyfikowane w rejestrowaniu ujawniają główną przyczynę problemu.

Jeśli tak nie jest, może zaistnieć konieczność zawężenia potencjalnych przyczyn, sprawdzając właściwości i elementy, które są danymi wejściowymi do zadania, którego wykonanie nie powiodło się.
