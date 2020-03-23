---
title: Zdarzenia kompilacji (Visual Basic) — Okno dialogowe
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4cd0a46e5ab4cc9c3a9e00773818d536b84891
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461449"
---
# <a name="build-events-dialog-box-visual-basic"></a>Zdarzenia kompilacji (Visual Basic) — Okno dialogowe

Okno dialogowe **Zdarzenia kompilacji** służy do określania instrukcji konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia przed kompilacją lub po kompilacji. Aby uzyskać więcej informacji, zobacz [Jak: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Wiersz polecenia zdarzenia przed kompilacją**

Określa wszystkie polecenia do wykonania przed rozpoczęciem kompilacji. Aby wpisać długie polecenia, kliknij przycisk **Edytuj wstępnie skompilować,** aby wyświetlić [okno dialogowe Wiersz polecenia zdarzenia przed kompilacją/po utworzeniu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i nie jest wyzwalana żadna kompilacja.

**Wiersz polecenia zdarzenia po kompilacji**

Określa wszystkie polecenia do wykonania po zakończeniu kompilacji. Aby wpisać długie polecenia, kliknij przycisk **Edytuj po kompilacji,** aby wyświetlić okno dialogowe **Wiersz polecenia zdarzenia przed kompilacją/po utworzeniu.**

> [!NOTE]
> Dodaj `call` instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki .bat. Na przykład: `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

**Uruchamianie zdarzenia po kompilacji**

Określa warunki uruchamiania zdarzenia po kompilacji, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**Zawsze**|Zdarzenie po kompilacji zostanie uruchomione, niezależnie od tego, czy kompilacja zakończy się pomyślnie.|
|**Na udanej kompilacji**|Zdarzenie po kompilacji zostanie uruchomione, jeśli kompilacja zakończy się pomyślnie. Zdarzenie zostanie uruchomione nawet dla projektu, który jest aktualny, tak długo, jak kompilacja powiedzie się. Jest to ustawienie domyślne.|
|**Gdy kompilacja aktualizuje dane wyjściowe projektu**|Zdarzenie po kompilacji będzie uruchamiane tylko wtedy, gdy plik wyjściowy kompilatora (exe lub .dll) różni się od poprzedniego pliku wyjściowego kompilatora. Zdarzenie po kompilacji nie jest uruchamiane, jeśli projekt jest aktualny.|

## <a name="see-also"></a>Zobacz też

- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Porady: określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Okno dialogowe Wiersz polecenia zdarzenia przed kompilacją/po utworzeniu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)