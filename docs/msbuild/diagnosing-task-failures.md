---
title: Diagnozowanie błędów zadań | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593281"
---
# <a name="diagnosing-task-failures"></a>Diagnozowanie błędów zadań

`MSB6006`jest emitowany, <xref:Microsoft.Build.Utilities.ToolTask>gdy klasa pochodna uruchamia proces narzędzia, który zwraca kod zakończenia niezerowej, jeśli zadanie nie rejestrowało bardziej szczegółowego błędu.

## <a name="identifying-the-failing-task"></a>Identyfikowanie zadania, które nie powiódł się

Po napotkaniu błędu zadania, pierwszym krokiem jest zidentyfikowanie zadania, które nie działa.

Tekst błędu określa nazwę narzędzia (przyjazną nazwę podana przez implementację <xref:Microsoft.Build.Utilities.ToolTask.ToolName> zadania lub nazwę pliku wykonywalnego) oraz numeryczny kod zakończenia. Na przykład w przeglądarce

```text
error MSB6006: "custom tool" exited with code 1.
```

Nazwa narzędzia `custom tool` jest i kod `1`zakończenia jest .

### <a name="command-line-builds"></a>Kompilacje wiersza polecenia

Jeśli kompilacja została skonfigurowana tak, aby zawierała podsumowanie (domyślne), podsumowanie będzie wyglądać następująco:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Ten wynik wskazuje, że wystąpił błąd w zadaniu zdefiniowanym `S:\MSB6006_demo\MSB6006_demo.csproj`w wierszu `InvokeToolTask`19 `S:\MSB6006_demo\MSB6006_demo.csproj`pliku , w miejscu docelowym o nazwie , w projekcie .

### <a name="in-visual-studio"></a>W programie Visual Studio

Te same informacje są dostępne na liście błędów `File`programu `Line`Visual Studio w kolumnach `Project`, i .

## <a name="finding-more-failure-information"></a>Znajdowanie więcej informacji o awarii

Ten błąd jest emitowany, gdy zadanie nie rejestrowało określonego błędu. Nie można zarejestrować błąd jest często, ponieważ zadanie nie jest skonfigurowany do zrozumienia formatu błędu emitowanego przez narzędzie, które wywołuje.

Dobrze zachowane narzędzia zazwyczaj emitują pewne informacje kontekstowe lub informacje o błędach do ich standardowego strumienia danych wyjściowych lub błędów, a zadania domyślnie przechwytują i rejestrują te informacje. Poszukaj we wpisach dziennika, zanim wystąpił błąd, aby uzyskać dodatkowe informacje. Ponowne uruchamianie kompilacji z wyższym poziomem dziennika może być wymagane, aby zachować te informacje.

## <a name="next-steps"></a>Następne kroki

Mam nadzieję, że dodatkowy kontekst lub błędy zidentyfikowane podczas rejestrowania ujawniają główną przyczynę problemu.

Jeśli nie, może być trzeba zawęzić potencjalne przyczyny, badając właściwości i elementy, które są dane wejściowe do zadania w przypadku awarii.
