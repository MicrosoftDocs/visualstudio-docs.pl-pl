---
title: Zaawansowane ustawienia zabezpieczeń — Okno dialogowe
description: Zaawansowane ustawienia zabezpieczeń — okno dialogowe pozwala określić ustawienia zabezpieczeń związane z debugowaniem w strefie.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ece930da2bb133a19e443da4d37654367a1c862
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868988"
---
# <a name="advanced-security-settings-dialog-box"></a>Zaawansowane ustawienia zabezpieczeń — Okno dialogowe

To okno dialogowe umożliwia określenie ustawień zabezpieczeń związanych z debugowaniem w strefie.

![Zaawansowane ustawienia zabezpieczeń — okno dialogowe w programie Visual Studio](../media/advanced-security-settings.png)

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **zabezpieczenia** . Na stronie **zabezpieczenia** wybierz opcję **Włącz ustawienia zabezpieczeń ClickOnce**, kliknij **to jest aplikacja częściowej relacji zaufania**, a następnie kliknij przycisk **Zaawansowane**.

## <a name="uielement-list"></a>Lista elementów UIElement

**Przyznaj aplikacji dostęp do jej lokalizacji pochodzenia**

Jeśli zaznaczysz to pole wyboru, aplikacja będzie mogła uzyskać dostęp do witryny sieci Web lub udziału serwera, na którym została opublikowana. Ta opcja jest wybrana domyślnie.

**Debuguj tę aplikację tak, jakby była pobrana z następującego adresu URL**

Jeśli musisz zezwolić aplikacji na dostęp do witryny sieci Web lub udziału serwera odpowiadającego **adresowi URL instalacji** określonym na stronie **publikowania** , wprowadź tutaj ten adres URL. Ta opcja jest dostępna tylko w przypadku wybrania opcji **Udziel dostępu aplikacji do jej lokalizacji pochodzenia** .

## <a name="see-also"></a>Zobacz też

- [Strona zabezpieczeń, Projektant projektu](../../ide/reference/security-page-project-designer.md)
