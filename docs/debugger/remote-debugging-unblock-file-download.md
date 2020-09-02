---
title: Odblokuj pobieranie zdalnych narzędzi
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62903030"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Instrukcje: Odblokowywanie pobierania narzędzi zdalnych w systemie Windows Server

Domyślne ustawienia zabezpieczeń w programie Internet Explorer w systemie Windows Server mogą spowodować czasochłonne pobieranie składników, takich jak narzędzia zdalne.

* Konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer, co uniemożliwia otwieranie witryn sieci Web i uzyskiwanie dostępu do zasobów internetowych, chyba że domena zawierająca zasób jest jawnie dozwolona (to jest zaufana). Mimo że to ustawienie można wyłączyć, nie jest to zalecane, ponieważ może stanowić zagrożenie bezpieczeństwa.

* W systemie Windows Server 2016 domyślne ustawienie **opcji Internet Opcje**  >  **zabezpieczeń**  >  **Internet**na  >  **poziomie niestandardowym**  >  **Downloads** powoduje także wyłączenie pobierania plików. Jeśli zdecydujesz się pobrać narzędzia zdalne bezpośrednio w systemie Windows Server, musisz włączyć pobieranie plików.

Aby pobrać narzędzia w systemie Windows Server, zalecamy jedną z następujących czynności:

* Pobierz narzędzia zdalne na innym komputerze, takim jak uruchomiony program Visual Studio, a następnie skopiuj plik *exe* do systemu Windows Server.

* Uruchom zdalny debuger [z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon) na komputerze z programem Visual Studio.

* Pobierz narzędzia zdalne bezpośrednio w systemie Windows Server i zaakceptuj odpowiednie instrukcje, aby dodać Zaufane witryny. Nowoczesne witryny sieci Web często zawierają wiele zasobów innych firm, dzięki czemu może to skutkować wieloma komunikatami. Ponadto może być konieczne ręczne dodanie wszelkich przekierowanych linków. Przed rozpoczęciem pobierania można dodać niektóre Zaufane witryny. Przejdź do **opcji internetowych > zabezpieczenia > zaufane lokacje > Lokacje** i Dodaj następujące lokacje.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * informacje: puste

  W przypadku starszych wersji debugera w systemie my.visualstudio.com Dodaj te dodatkowe lokacje, aby upewnić się, że logowanie zakończyło się pomyślnie:

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

    Jeśli zdecydujesz się dodać te domeny podczas pobierania narzędzi zdalnych, wybierz opcję **Dodaj** po wyświetleniu monitu.

    ![Zablokowana zawartość — okno dialogowe](../debugger/media/remotedbg-blocked-content.png)

    Po pobraniu oprogramowania otrzymujesz dodatkowe żądania, aby udzielić uprawnień do ładowania różnych skryptów i zasobów witryny sieci Web. W systemie my.visualstudio.com zalecamy dodanie dodatkowych domen, aby upewnić się, że logowanie zakończyło się pomyślnie.