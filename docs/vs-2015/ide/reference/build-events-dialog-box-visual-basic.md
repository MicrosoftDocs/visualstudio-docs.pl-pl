---
title: Okno dialogowe zdarzenia kompilacji (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9fa3b4365f49d172e077ca132b26a49580228c25
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660958"
---
# <a name="build-events-dialog-box-visual-basic"></a>Zdarzenia kompilacji (Visual Basic) — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą okna dialogowego **zdarzenia kompilacji** można określić instrukcje konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia przed kompilacją lub po kompilacji. Aby uzyskać więcej informacji, zobacz [How to: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

 **Wiersz polecenia zdarzenia przed kompilacją** Określa wszystkie polecenia do wykonania przed rozpoczęciem kompilacji. Aby wpisać długie polecenia, kliknij opcję **Edytuj przed kompilacją** , aby wyświetlić okno [dialogowe zdarzenie sprzed kompilacji/zdarzenie po kompilacji](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i żadna kompilacja nie zostanie wyzwolona.

 **Wiersz polecenia zdarzenia po kompilacji** Określa wszystkie polecenia do wykonania po zakończeniu kompilacji. Aby wpisać długie polecenia, kliknij przycisk **Edytuj po kompilacji** , aby wyświetlić **zdarzenie sprzed kompilacji/wiersz polecenia w**ialog.

> [!NOTE]
> Dodaj instrukcję `call` przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki. bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Uruchom zdarzenie po kompilacji** Określa warunki dla zdarzenia po kompilacji do uruchomienia, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**Stałego**|Zdarzenie po kompilacji zostanie uruchomione, niezależnie od tego, czy kompilacja zakończy się powodzeniem.|
|**Po pomyślnej kompilacji**|Zdarzenie po kompilacji zostanie uruchomione, jeśli kompilacja zakończy się pomyślnie. Zdarzenie zostanie uruchomione nawet dla projektu, który jest aktualny, o ile kompilacja zakończy się powodzeniem. To jest ustawienie domyślne.|
|**Gdy kompilacja aktualizuje dane wyjściowe projektu**|Zdarzenie po kompilacji zostanie uruchomione tylko wtedy, gdy plik wyjściowy kompilatora (. exe lub. dll) różni się od poprzedniego pliku wyjściowego kompilatora. Zdarzenie po kompilacji nie jest uruchamiane, jeśli projekt jest aktualny.|

## <a name="see-also"></a>Zobacz też
 [Strona kompilacji, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [okno dialogowe zdarzenia sprzed kompilacji/zdarzenia po kompilacji](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
