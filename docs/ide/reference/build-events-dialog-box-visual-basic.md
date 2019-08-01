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
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461449"
---
# <a name="build-events-dialog-box-visual-basic"></a>Zdarzenia kompilacji (Visual Basic) — Okno dialogowe

Za pomocą okna dialogowego **zdarzenia kompilacji** można określić instrukcje konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia przed kompilacją lub po kompilacji. Aby uzyskać więcej informacji, zobacz [jak: Określ zdarzenia kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Wiersz polecenia zdarzenia przed kompilacją**

Określa wszystkie polecenia do wykonania przed rozpoczęciem kompilacji. Aby wpisać długie polecenia, kliknij opcję **Edytuj przed kompilacją** , aby wyświetlić okno [dialogowe zdarzenie sprzed kompilacji/zdarzenie po kompilacji](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i żadna kompilacja nie zostanie wyzwolona.

**Wiersz polecenia zdarzenia po kompilacji**

Określa wszystkie polecenia do wykonania po zakończeniu kompilacji. Aby wpisać długie polecenia, kliknij przycisk **Edytuj po kompilacji** , aby wyświetlić okno dialogowe **zdarzenie przed kompilacją/zdarzenie po kompilacji** .

> [!NOTE]
> `call` Dodaj instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki. bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

**Uruchom zdarzenie po kompilacji**

Określa warunki dla zdarzenia po kompilacji do uruchomienia, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**Stałego**|Zdarzenie po kompilacji zostanie uruchomione, niezależnie od tego, czy kompilacja zakończy się powodzeniem.|
|**Po pomyślnej kompilacji**|Zdarzenie po kompilacji zostanie uruchomione, jeśli kompilacja zakończy się pomyślnie. Zdarzenie zostanie uruchomione nawet dla projektu, który jest aktualny, o ile kompilacja zakończy się powodzeniem. To jest ustawienie domyślne.|
|**Gdy kompilacja aktualizuje dane wyjściowe projektu**|Zdarzenie po kompilacji zostanie uruchomione tylko wtedy, gdy plik wyjściowy kompilatora (. exe lub. dll) różni się od poprzedniego pliku wyjściowego kompilatora. Zdarzenie po kompilacji nie jest uruchamiane, jeśli projekt jest aktualny.|

## <a name="see-also"></a>Zobacz także

- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Wiersz polecenia zdarzenia sprzed kompilacji/zdarzenia po kompilacji, okno dialogowe](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)