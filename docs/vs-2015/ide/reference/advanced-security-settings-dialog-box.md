---
title: Zaawansowane ustawienia zabezpieczeń — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 000c3c4e2996869e96fd0d6097b5bab8576936a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651740"
---
# <a name="advanced-security-settings-dialog-box"></a>Zaawansowane ustawienia zabezpieczeń — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

To okno dialogowe umożliwia określenie ustawień zabezpieczeń związanych z debugowaniem w strefie.

 Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **zabezpieczenia** . Na stronie **zabezpieczenia** wybierz opcję **Włącz ustawienia zabezpieczeń ClickOnce**, kliknij **to jest aplikacja częściowej relacji zaufania**, a następnie kliknij przycisk **Zaawansowane**.

## <a name="uielement-list"></a>Lista elementów UI
 **Debuguj tę aplikację z wybranym zestawem uprawnień** Jeśli zaznaczysz to pole wyboru, zestaw uprawnień wybrany na stronie **zabezpieczenia** jest używany podczas debugowania. Ta opcja jest wybrana domyślnie.

 Aby debugowanie w strefie zabezpieczeń działało, należy włączyć tę opcję. Ponadto należy włączyć opcję **Włącz proces hostingu programu Visual Studio** (dostępną na stronie **debugowania** **projektanta projektu**).

 W przypadku projektów aplikacji przeglądarki sieci Web WPF opcja **Debuguj tę aplikację z wybranym zestawem uprawnień** jest zaznaczona i wyłączona.

 **Przyznaj aplikacji dostęp do jej lokalizacji pochodzenia** Jeśli zaznaczysz to pole wyboru, aplikacja będzie mogła uzyskać dostęp do witryny sieci Web lub udziału serwera, na którym jest publikowany. Ta opcja jest wybrana domyślnie.

 **Debuguj tę aplikację tak, jakby była pobrana z następującego adresu URL** Jeśli musisz zezwolić aplikacji na dostęp do witryny sieci Web lub udziału serwera odpowiadającego **adresowi URL instalacji** określonym na stronie **Publikuj** , wpisz tutaj ten adres URL. Ta opcja jest dostępna tylko w przypadku wybrania opcji **Udziel dostępu aplikacji do jej lokalizacji pochodzenia** .

## <a name="see-also"></a>Zobacz też
 [Strona zabezpieczeń, Projektant projektu](../../ide/reference/security-page-project-designer.md)
