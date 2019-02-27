---
title: Konfigurowanie repozytorium podwersji
description: Za pomocą rozwiązania Subversion w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 7dfb5c645125afc1485c1422909e52741507b327
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56953690"
---
# <a name="set-up-a-subversion-repository"></a>Konfigurowanie repozytorium podwersji

Subversion to scentralizowana _system kontroli wersji_, co oznacza, że istnieje pojedynczego serwera, który zawiera wszystkie pliki i wersje, od których użytkowników można wyewidencjonować dowolną wersję każdego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium systemu Subversion, użytkownik pobiera migawkę repozytorium w danym momencie.

Aby używać rozwiązania Subversion dla kontroli wersji, należy można zainstalować na komputerze. Aby sprawdzić, czy Subversion jest zainstalowany ten komputer, użyj następującego polecenia w terminalu:

```bash
svn --version
```

To polecenie zwraca numer wersji.

Jeśli Subversion nie jest już zainstalowany, najprostszym sposobem jego jest po zainstalowaniu _narzędzi wiersza polecenia narzędzia Xcode_. Użyj poniższego polecenia, aby zainstalować narzędzia wiersza polecenia programu Xcode i Subversion.

```bash
xcode-select --install
```

Po zainstalowaniu systemu Subversion na maszynie, wykonaj następujące kroki, aby opublikować projekt w SVN.

1. Utwórz bezpłatne repozytorium SVN w trybie online. W tym przykładzie [Assembla](https://app.assembla.com/) był używany. Po utworzeniu, być podany adres URL, który będzie służyć do nawiązać połączenie z repozytorium:

    ![Skopiuj adres URL SVN](media/version-control-subversion1-sml.png)

2. Otwórz lub Utwórz programu Visual Studio dla komputerów Mac projektu.

3. Kliknij prawym przyciskiem myszy projekt i wybierz pozycję **kontroli wersji > Publikuj w kontroli wersji...** :

    ![Rozpocznij publikowanie projektu](media/version-control-subversion2.png)

4. W **nawiązywanie połączenia z repozytorium** zaznacz **Subversion** od góry listy rozwijanej.

5. Wprowadź adres URL w kroku 1. Po wprowadzeniu adresu URL inne pola są wypełniane przez domyślny:

    ![Wybierz repozytorium, a następnie wprowadź szczegóły okna dialogowego](media/version-control-subversion3.png)

7. Kliknij przycisk **OK** , a następnie potwierdź, naciskając klawisz **Publikuj**.

7. Po wyświetleniu monitu wprowadź swoje poświadczenia dla lokacji, na którym utworzono repozytorium, jak przedstawiono poniżej:

    ![Wprowadzanie poświadczeń repozytorium subversion](media/version-control-subversion5.png)

8. Wszystkie polecenia kontroli wersji dostępna powinno być teraz widoczne w menu kontroli wersji.

## <a name="see-also"></a>Zobacz także

- [Praca z podwersją](working-with-subversion.md)