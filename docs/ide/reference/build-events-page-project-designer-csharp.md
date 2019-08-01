---
title: Strona Zdarzenia kompilacji, Projektant projektu (C#)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba429c116d44a5d79d935fe3a1ad07b6d5f36f79
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461852"
---
# <a name="build-events-page-project-designer-c"></a>Strona Zdarzenia kompilacji, Projektant projektu (C#)

Użyj strony **zdarzenia kompilacji** **projektanta projektu** , aby określić instrukcje konfiguracji kompilacji. Możesz również określić warunki, w których są uruchamiane wszystkie zdarzenia po kompilacji. Aby uzyskać więcej informacji, zobacz [jak: Określ zdarzenia kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)i [instrukcje: Określ zdarzenia kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Lista elementów UI

**Konfiguracja**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [stronę Kompilacja, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Platformach**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [stronę Kompilacja, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Wiersz polecenia zdarzenia przed kompilacją**

Określa wszystkie polecenia do wykonania przed rozpoczęciem kompilacji. Aby wpisać długie polecenia, kliknij opcję **Edytuj przed kompilacją** , aby wyświetlić okno [dialogowe zdarzenie sprzed kompilacji/zdarzenie po kompilacji](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i żadna kompilacja nie zostanie wyzwolona.

**Wiersz polecenia zdarzenia po kompilacji**

Określa wszystkie polecenia do wykonania po zakończeniu kompilacji. Aby wpisać długie polecenia, kliknij przycisk **Edytuj po kompilacji** , aby wyświetlić okno **dialogowe zdarzenie przed kompilacją/zdarzenie po kompilacji**.

> [!NOTE]
> `call` Dodaj instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki. bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

**Uruchom zdarzenie po kompilacji**

Określa następujące warunki dla zdarzenia po kompilacji do uruchomienia, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**Stałego**|Zdarzenie po kompilacji zostanie uruchomione bez względu na to, czy kompilacja powiodła się.|
|**Po pomyślnej kompilacji**|Zdarzenie po kompilacji zostanie uruchomione, jeśli kompilacja zakończy się pomyślnie. W tym celu zdarzenie zostanie uruchomione nawet dla projektu, który jest aktualny, o ile kompilacja zakończy się powodzeniem.|
|**Gdy kompilacja aktualizuje dane wyjściowe projektu**|Zdarzenie po kompilacji zostanie uruchomione tylko wtedy, gdy plik wyjściowy kompilatora (. exe lub. dll) różni się od poprzedniego pliku wyjściowego kompilatora. W rezultacie zdarzenie po kompilacji nie jest uruchamiane, jeśli projekt jest aktualny.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Instrukcje: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)