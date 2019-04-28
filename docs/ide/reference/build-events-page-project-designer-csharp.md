---
title: Strona Zdarzenia kompilacji, Projektant projektu (C#)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 25ea62284698de9d57cbcbefa73b950af8c42a6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790905"
---
# <a name="build-events-page-project-designer-c"></a>Strona Zdarzenia kompilacji, Projektant projektu (C#)
Użyj **zdarzenia kompilacji** strony **projektanta projektu** do określenia instrukcje dotyczące konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia mające miejsce po kompilacji. Aby uzyskać więcej informacji, zobacz [jak: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)i [jak: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Lista elementów UI
 **Konfiguracja** ten formant nie jest edytowalny na tej stronie. Aby uzyskać opis tego formantu, zobacz [Stroka kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma** ten formant nie jest edytowalny na tej stronie. Aby uzyskać opis tego formantu, zobacz [Stroka kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Wiersz polecenia zdarzenia sprzed kompilacji** określa dowolnych poleceń do wykonania przed rozpoczęciem kompilacji. Do typu long polecenia, kliknij przycisk **Edytuj prekompilacji** do wyświetlenia [prekompilacji zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Jeśli projekt jest aktualny, a nie kompilacja zostaje wyzwolona, nie należy uruchamiać zdarzenia prekompilacyjnego.

 **Wiersz polecenia zdarzenia po kompilacji** określa dowolnych poleceń do wykonania po zakończeniu kompilacji. Do typu long polecenia, kliknij przycisk **edytować po kompilacji** do wyświetlenia **prekompilacji zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe**.

> [!NOTE]
> Dodaj `call` instrukcję przed polecenia wszystkich wykonywanych po kompilacji, które uruchamiają pliki bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Uruchom zdarzenie po kompilacji** określa następujące warunki dla zdarzenia postkompilacyjnego do uruchomienia, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**zawsze**|Zdarzenie po kompilacji zostaną uruchomione niezależnie od tego, czy kompilacja zakończy się pomyślnie.|
|**W przypadku pomyślnej kompilacji**|Zdarzenie po kompilacji będzie działać, jeśli kompilacja zakończy się pomyślnie. W związku z tym zdarzenia uruchomią się nawet w przypadku projektu, który jest aktualne, tak długo, jak kompilacja zakończy się pomyślnie.|
|**Gdy kompilacja aktualizuje dane wyjściowe projektu**|Zdarzenie po kompilacji zostanie uruchomiona tylko w sytuacji, gdy plik wyjściowy kompilatora (.exe lub .dll) różni się od poprzedniego pliku danych wyjściowych kompilatora. W związku z tym zdarzenia postkompilacyjnego nie zostanie uruchomione, gdy projekt jest aktualny.|

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Instrukcje: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)