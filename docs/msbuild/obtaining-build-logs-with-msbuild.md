---
title: Uzyskiwanie kompilacja dzienników za pomocą narzędzia MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7999e65a36968872816abfa8246c0e42ce699d3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627366"
---
# <a name="obtain-build-logs-with-msbuild"></a>Uzyskiwanie dzienników kompilacji za pomocą narzędzia MSBuild

Za pomocą przełączników za pomocą narzędzia MSBuild, można określić ilość danych kompilacji, aby Przegląd i czy chcesz zapisać dane kompilacji do jednego lub więcej plików. Można również określić niestandardowe rejestratora zbierania danych o kompilacji. Aby uzyskać informacje dotyczące przełączników wiersza polecenia programu MSBuild, które ten temat nie obejmuje, zobacz [wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Jeśli tworzysz projektów za pomocą programu Visual Studio IDE tych kompilacji można rozwiązać, przeglądając dzienniki kompilacji. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="set-the-level-of-detail"></a>Ustaw poziom szczegółowości

 Gdy tworzysz projekt za pomocą programu MSBuild bez określania poziomu szczegółowości zostaną wyświetlone następujące informacje w dzienniku danych wyjściowych:

- Błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne.

- Niektóre zdarzenia stanu.

- Podsumowanie kompilacji.

Za pomocą **— poziom szczegółowości** (**- v**) przełączyć, można kontrolować, jak dużo danych pojawia się w dzienniku danych wyjściowych. Do rozwiązywania problemów, należy użyć poziom szczegółowości, albo `detailed` (`d`) lub `diagnostic` (`diag`), zapewniającą najwięcej informacji.

Proces kompilacji może być niższa, po ustawieniu **— poziom szczegółowości** do `detailed` i nawet wolniej, po ustawieniu **— poziom szczegółowości** do `diagnostic`.

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Ustawienia poziomu szczegółowości

W poniższej tabeli przedstawiono, jaki poziom szczegółowości dziennika (wartości kolumn) ma wpływ na jakie rodzaje komunikatów (wartości wierszy) są rejestrowane.

|                                       | Quiet | Minimalny | Normalne | Szczegółowe | Diagnostyka |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| błędy                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Ostrzeżenia                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Komunikaty o wysokiej ważności              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Normalny znaczenie wiadomości           |       |         |    ✅   |     ✅    |      ✅     |
| Komunikaty o niskiej ważności              |       |         |        |     ✅    |      ✅     |
| Dodatkowe informacje aparatu MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Zapisz w pliku dziennika kompilacji

Możesz użyć **- fileLogger** (**fl**) przełącznik, aby zapisać dane kompilacji do pliku. Poniższy przykład zapisuje dane kompilacji do pliku, który nosi nazwę *msbuild.log*.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 W poniższym przykładzie plik dziennika o nazwie *MyProjectOutput.log*, a poziom szczegółowości danych wyjściowych dziennika jest ustawione na `diagnostic`. Należy określić te dwa ustawienia za pomocą **- filelogparameters** (`flp`) przełącznika.

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="save-the-log-output-to-multiple-files"></a>Zapisz dane wyjściowe dziennika do wielu plików

 Poniższy przykład zapisuje cały dziennik, aby *msbuild1.log*, po prostu błędy do *JustErrors.log*i po prostu ostrzeżeń do *JustWarnings.log*. W przykładzie użyto liczby plików dla każdego z trzech plików. Liczby plików są określane tylko po **-fl** i **- flp** przełączników (na przykład `-fl1` i `-flp1`).

 **- Filelogparameters** (`flp`) przełącza dla plików, 2 i 3, określ, jakie nazwę każdego pliku i co należy uwzględnić w każdym pliku. Nie określono nazwy dla pliku 1, więc domyślną nazwę *msbuild1.log* jest używany.

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="save-a-binary-log"></a>Zapisz dziennik binarny

Możesz zapisać dziennik w skompresowany, binarny format za pomocą **- binaryLogger** (**bl**) przełącznika. Ten dziennik zawiera szczegółowy opis procesu kompilacji i może zostać odczytany przez niektóre narzędzia analizy dzienników.

W poniższym przykładzie tworzony jest plik binarny dziennika o nazwie *binarylogfilename*.

```cmd
/bl:binarylogfilename.binlog
```

Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="use-a-custom-logger"></a>Użyj niestandardowego rejestrowania

 Można napisać własne rejestratora, tworząc typ zarządzany, który implementuje <xref:Microsoft.Build.Framework.ILogger> interfejsu. Można na przykład użyć Rejestrator niestandardowych, wysłać błędy kompilacji w wiadomości e-mail, rejestrować je do bazy danych lub dziennika je do pliku XML. Aby uzyskać więcej informacji, zobacz [rejestratory kompilacji](../msbuild/build-loggers.md).

 W wierszu polecenia programu MSBuild, należy określić Rejestrator niestandardowych za pomocą **-rejestratora** przełącznika. Można również użyć **- noconsolelogger** przełącznik wyłączający rejestratora konsoli do domyślnego.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Rejestratory kompilacji](../msbuild/build-loggers.md)
- [Logowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md)
- [Tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)