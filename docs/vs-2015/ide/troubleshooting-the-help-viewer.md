---
title: Rozwiązywanie problemów z podglądem pomocy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 490525cded11a4cddbbfb3f650d87c55b2fa196b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654775"
---
# <a name="troubleshooting-the-help-viewer"></a>Rozwiązywanie problemów z Podglądem Pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono problemy, które mogą wystąpić w programie Podgląd pomocy.

## <a name="audio-doesnt-work"></a>Dźwięk nie działa.
 Podgląd pomocy nie obejmuje odtwarzacza audio. Jeśli pobierasz zawartość zawierającą dźwięk i nic się nie dzieje, gdy wybierzesz opcję **Odtwórz**, zainstaluj odtwarzacz audio.

## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>Wyszukiwanie nie działa w systemie Windows Server 2008, Windows Server 2008 z dodatkiem SP1 lub Windows Server 2008 R2.
 Funkcje wyszukiwania i filtrowania w podglądzie pomocy wymagają zainstalowania i włączenia usługi wyszukiwania systemu Windows. Domyślnie ta usługa jest wyłączona w systemie Windows Server 2008, Windows Server 2008 z dodatkiem Service Pack 1 (SP1) i Windows Server 2008 R2.

#### <a name="to-activate-windows-search-service"></a>Aby aktywować usługę wyszukiwania systemu Windows

1. Rozpocznij Menedżer serwera.

2. W okienku nawigacji po lewej stronie wybierz pozycję **role**.

3. W okienku Podsumowanie ról wybierz pozycję **Dodaj rolę**.

4. Wybierz rolę usługi plików, a następnie wybierz przycisk **dalej** .

5. Wybierz usługę roli wyszukiwania systemu Windows.

## <a name="additional-resources"></a>Dodatkowe zasoby
 Aby uzyskać więcej informacji i przekazać opinię na temat pomocy, możesz skorzystać z następujących zasobów:

- Aby przekazać opinię, zobacz [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) w witrynie internetowej firmy Microsoft lub Wyślij wiadomość e-mail do [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).

- Aby uzyskać więcej informacji, zapoznaj się z [dokumentacją dla deweloperów i forum systemu pomocy](http://go.microsoft.com/fwlink/?LinkId=232741) oraz blog [pomocy Guy](http://go.microsoft.com/fwlink/?LinkId=232743) .

## <a name="see-also"></a>Zobacz też
 [Podręcznik administratora programu Help Viewer 2,1](http://go.microsoft.com/fwlink/?LinkId=243985)
