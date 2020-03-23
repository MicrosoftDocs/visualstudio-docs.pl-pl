---
title: Uzyskiwanie dzienników kompilacji za pomocą msbuild | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f756d432d9ff4d3824c1f1165c63710e4d10c2e9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594893"
---
# <a name="obtain-build-logs-with-msbuild"></a>Uzyskiwanie dzienników kompilacji za pomocą usługi MSBuild

Za pomocą przełączników z MSBuild, można określić, ile danych kompilacji, które mają zostać przejrzane i czy chcesz zapisać dane kompilacji do jednego lub więcej plików. Można również określić rejestratora niestandardowego do zbierania danych kompilacji. Aby uzyskać informacje o przełącznikach wiersza polecenia MSBuild, których nie dotyczy ten temat, zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Jeśli tworzysz projekty przy użyciu środowiska IDE programu Visual Studio, można rozwiązać te kompilacje, przeglądając dzienniki kompilacji. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="set-the-level-of-detail"></a>Ustawianie poziomu szczegółowości

 Podczas tworzenia projektu przy użyciu MSBuild bez określania poziomu szczegółowości, następujące informacje są wyświetlane w dzienniku danych wyjściowych:

- Błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne.

- Niektóre zdarzenia stanu.

- Podsumowanie kompilacji.

Za pomocą przełącznika **-verbosity** (**-v**), można kontrolować, ile danych pojawia się w dzienniku danych wyjściowych. Aby rozwiązać problem, należy użyć poziomu `detailed` szczegółowości`d`jednego `diagnostic` `diag`( ) lub ( ), który zawiera najwięcej informacji.

Proces kompilacji może być wolniejszy po ustawieniu `detailed` **-verbosity** do, a nawet wolniej po ustawieniu **-verbosity** do `diagnostic`.

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Ustawienia szczegółowości

W poniższej tabeli pokazano, jak szczegółowość dziennika (wartości kolumn) wpływa na typy wiadomości (wartości wierszy) są rejestrowane.

|                                       | Quiet | Minimalny | Normalne | szczegółowo | Diagnostyczne |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Errors                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Ostrzeżenia                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Wiadomości o dużym znaczeniu              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Wiadomości o normalnej ważności           |       |         |    ✅   |     ✅    |      ✅     |
| Wiadomości o niskim znaczeniu              |       |         |        |     ✅    |      ✅     |
| Dodatkowe informacje o silniku MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Zapisywanie dziennika kompilacji w pliku

Można użyć przełącznika **-fileLogger** (**fl**), aby zapisać dane kompilacji w pliku. W poniższym przykładzie zapisuje dane kompilacji do pliku o nazwie *msbuild.log*.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 W poniższym przykładzie plik dziennika nosi nazwę *MyProjectOutput.log,* a szczegółowość danych `diagnostic`wyjściowych dziennika jest ustawiona na . Te dwa ustawienia można określić za pomocą **przełącznika -filelogparameters** (`flp`).

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Aby uzyskać więcej informacji, zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="save-the-log-output-to-multiple-files"></a>Zapisywanie danych wyjściowych dziennika w wielu plikach

 Poniższy przykład zapisuje cały dziennik do *msbuild1.log*, tylko błędy *JustErrors.log*, i tylko ostrzeżenia *justwarnings.log*. W przykładzie użyto numerów plików dla każdego z trzech plików. Numery plików są określane tuż po przełącznikach **-fl** i **-flp** (na przykład `-fl1` i `-flp1`).

 Przełączniki **-filelogparameters** (`flp`) dla plików 2 i 3 określają, co należy nazwać każdy plik i co należy uwzględnić w każdym pliku. Dla pliku 1 nie określono nazwy, dlatego używana jest domyślna nazwa *pliku msbuild1.log.*

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Aby uzyskać więcej informacji, zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="save-a-binary-log"></a>Zapisywanie dziennika binarnego

Dziennik można zapisać w skompresowanym formacie binarnym za pomocą przełącznika **-binaryLogger** (**bl).** Ten dziennik zawiera szczegółowy opis procesu kompilacji i może być odczytywany przez niektóre narzędzia analizy dziennika.

W poniższym przykładzie tworzony jest binarny plik dziennika o nazwie *binarylogfilename*.

```cmd
-bl:binarylogfilename.binlog
```

Aby uzyskać więcej informacji, zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="use-a-custom-logger"></a>Używanie rejestratora niestandardowego

 Można napisać własny rejestrator, tworząc typ zarządzany, który <xref:Microsoft.Build.Framework.ILogger> implementuje interfejs. Można użyć rejestratora niestandardowego, na przykład, aby wysłać błędy kompilacji w wiadomości e-mail, zalogować je do bazy danych lub zalogować je do pliku XML. Aby uzyskać więcej informacji, zobacz [Tworzenie rejestratorów](../msbuild/build-loggers.md).

 W wierszu polecenia MSBuild należy określić rejestratora niestandardowego za pomocą przełącznika **-logger.** Można również użyć przełącznika **-noconsolelogger,** aby wyłączyć domyślny rejestrator konsoli.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Tworzenie rejestratorów](../msbuild/build-loggers.md)
- [Logowanie w środowisku wieloprocesorowym](../msbuild/logging-in-a-multi-processor-environment.md)
- [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
