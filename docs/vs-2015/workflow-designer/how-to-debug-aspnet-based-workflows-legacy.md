---
title: 'Instrukcje: debugowanie przepływów pracy opartych na ASP.NET (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668659"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Instrukcje: debugowanie przepływów pracy opartych na ASP.NET (starsza wersja)
W tym temacie opisano sposób debugowania aplikacji [!INCLUDE[wf](../includes/wf-md.md)] opartych na [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]ach przeznaczonych dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] w starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)].

 Można debugować starsze przepływy pracy uruchamiane w ASP.NET lub starszych przepływach pracy, które są publikowane jako usługa sieci Web przez dołączenie do procesu, w którym przepływ pracy jest hostowany.

### <a name="to-debug-an-aspnet-based-workflow"></a>Aby debugować przepływ pracy oparty na ASP.NET

1. Włącz debugowanie dla aplikacji ASP.NET przez ustawienie w pliku Web. config opcji **debug = true** .

2. Ustaw bibliotekę przepływów pracy jako projekt startowy, a następnie ustaw punkty przerwania w przepływie pracy.

3. Wprowadź adres URL domyślnej strony sieci Web w oknie **dialogowym właściwości projektu** przepływu pracy **Uruchom przeglądarkę z zewnętrznym adresem URL** .

4. Wybierz pozycję **Dołącz do procesu** w menu **Debuguj** .

5. Wybierz proces do dołączenia z listy **dostępne procesy** .

     Dołącz do procesu w3wp. exe, webdev. WebServer lub proces aspnet_wp, w którym jest hostowany przepływ pracy.

6. Kliknij przycisk **zaznacz** obok pola tekstowego **Dołącz do** .

     Zostanie wyświetlone okno dialogowe **Wybieranie typu kodu** .

7. Wybierz kolejno opcje **Debuguj te typy kodu** i wybierz **przepływ pracy**.

8. Kliknij przycisk **OK**.

9. Kliknij przycisk **Dołącz**.

10. Otwórz domyślną stronę sieci Web w przeglądarce i Uruchom przepływ pracy.

## <a name="see-also"></a>Zobacz też
 [Wywoływanie debugera programu Visual Studio dla Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [instrukcje: ustawianie punktów przerwania w przepływach pracy (starsza wersja)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [debugowanie starszych przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)