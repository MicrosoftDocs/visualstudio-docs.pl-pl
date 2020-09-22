---
title: require-mssql
description: Narzędzie devinit wymaga — MSSQL.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2ad02a29b8ea8b59abd4f246c5cc1d206451d3fc
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005191"
---
# <a name="require-mssql"></a>require-mssql

`require-mssql`Narzędzie służy do instalowania [Microsoft SQL Server 2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) za pośrednictwem protokołu MS SQL Server ISO. Program SQL Server będzie dostępny przy `localhost` użyciu zintegrowanego uwierzytelniania systemu Windows. serwer SQL będzie dostępny z parametrami połączenia `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                   |
| [**klawiatur**](#input)                              | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                                                  |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.              |

### <a name="input"></a>Dane wejściowe

`input`Właściwość może być ciągiem z jedną z dwóch wartości:

| Wartość     | Opis                              |
|-----------|------------------------------------------|
| install   | Instaluje program SQL Server.                     |
| odinstalować | Odinstalowuje wszystkie instalacje programu SQL Server. |

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `require-mssql` narzędzia jest zainstalowanie programu SQL Server.

### <a name="builtin-options"></a>Wbudowane opcje

`require-mssql`Narzędzie ustawia liczbę argumentów wiersza polecenia Instalatora, aby upewnić się, że Instalator może uruchomić bezobsługowy. Te argumenty są wymienione poniżej, a dokumentacja na nich znajduje się w [dokumentacji instalacji programu SQL Server](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true).

| Nazwa                                                               | Opis |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION = Zainstaluj                                                    |             |
| /FEATURES = SQLEngine, LocalDB                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource = MU                                                   |             |
| /X86 = FAŁSZ                                                         |             |
| /INSTANCENAME = MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR = "C:\Program Files\Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR = "C:\Program Files (x86) \Microsoft SQL Server" |             |
| /SQLSVCINSTANTFILEINIT = true                                        |             |
| /INSTANCEDIR = "C:\Program Files\Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT = "NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE = ręczne                                          |             |
| /SQLSVCSTARTUPTYPE = automatyczne                                       |             |
| /SQLCOLLATION = "SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT = "NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS = Administratorzy                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs MSSQL.",
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```
