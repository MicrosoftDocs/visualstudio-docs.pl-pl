---
title: Odblokuj pobieranie narzędzi zdalnych
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988145"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Instrukcje: Odblokuj pobierania narzędzia zdalnej w systemie Windows Server

Domyślne ustawienia zabezpieczeń w programie Internet Explorer w systemie Windows Server można tworzyć i czasochłonne pobrać składników, takich jak remote tools.

* Włączeniu konfiguracji zwiększonych zabezpieczeń programu Internet Explorer, która uniemożliwia otwarcie witryny sieci Web i uzyskiwanie dostępu do zasobów sieci web, chyba że domenę zawierającą zasobu jest jawnie dozwolone (to znaczy, że zaufane). Mimo że to ustawienie zostanie wyłączone, nie zalecamy tego, ponieważ może on stwarzać zagrożenie bezpieczeństwa.

* W systemie Windows Server 2016, domyślne ustawienie w **Opcje internetowe** > **zabezpieczeń** > **Internet**  >   **Poziom niestandardowy** > **pliki do pobrania** również wyłącza pobierania plików. Jeśli wybierzesz pobieranie narzędzi zdalnych bezpośrednio w systemie Windows Server, należy włączyć pobieranie plików.

Aby pobrać narzędzia w systemie Windows Server, zaleca się jedną z następujących czynności:

* Pobieranie narzędzi zdalnych na innym komputerze, takie jak jednego uruchomionego programu Visual Studio, a następnie skopiuj *.exe* plików do systemu Windows Server.

* Uruchom zdalny debuger [z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon) na komputerze programu Visual Studio.

* Pobierz narzędzia zdalne bezpośrednio w systemie Windows Server i akceptowanie poleceń, aby dodać Zaufane witryny. Nowoczesnych witryn internetowych często zawierają wiele innych zasobów, więc może to spowodować wiele monitów. Ponadto wszystkie linki przekierowanego może być konieczne należy dodać ręcznie. Można dodać niektóre Zaufane witryny przed rozpoczęciem pobierania. Przejdź do **Opcje internetowe > Zabezpieczenia > Zaufane witryny > witryny** i dodaj następujące witryny.

  * VisualStudio.microsoft.com
  * download.visualstudio.microsoft.com
  * temat: puste

  Dla starszych wersji debugera na my.visualstudio.com Dodaj te dodatkowe lokacje, aby upewnić się, że ten użytkownik zaloguje się ponownie:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Jeśli możesz dodać te domeny podczas pobierania narzędzi zdalnych, a następnie wybierz **Dodaj** po wyświetleniu monitu.

    ![Okno dialogowe zawartości zablokowane](../debugger/media/remotedbg-blocked-content.png)

    Po pobraniu oprogramowania, możesz uzyskać niektóre dodatkowe żądania, aby przyznać uprawnienie do ładowania różnych skrypty witryny sieci web i zasobami. Na my.visualstudio.com zaleca się, że dodasz dodatkowe domeny, aby upewnić się, że ten użytkownik zaloguje się ponownie.