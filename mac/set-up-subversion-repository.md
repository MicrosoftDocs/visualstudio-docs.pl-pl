---
title: Konfigurowanie repozytorium podwersji
description: Korzystanie z Subversion w programie Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 7d95c73b8d745826b256d515f161194ee9dbb587
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692382"
---
# <a name="set-up-a-subversion-repository"></a>Konfigurowanie repozytorium Subversion

Subversion to scentralizowany _system kontroli wersji,_ co oznacza, że istnieje jeden serwer, który zawiera wszystkie pliki i poprawki, z których użytkownicy mogą sprawdzić dowolną wersję dowolnego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium Subversion, użytkownik pobiera migawkę repozytorium w tym momencie.

Aby użyć Subversion do kontroli wersji, musi być zainstalowany na komputerze. Aby sprawdzić, czy urządzenie Subversion jest zainstalowane, użyj następującego polecenia w terminalu:

```bash
svn --version
```

To polecenie zwraca numer wersji.

Jeśli Subversion nie jest jeszcze zainstalowany, najprostszym sposobem, aby go uzyskać jest zainstalowanie _narzędzia wiersza polecenia Xcode_. Użyj poniższego polecenia, aby zainstalować narzędzia Xcode Command Line Tools i Subversion.

```bash
xcode-select --install
```

Po zainstalowaniu subwersji na komputerze, należy wykonać następujące kroki, aby opublikować projekt w SVN.

1. Stwórz darmowe repozytorium SVN online. W tym przykładzie [użyto Assembla.](https://app.assembla.com/) Po utworzeniu zostanie podany adres URL, który będzie używany do łączenia się z repozytorium:

    ![kopiowanie adresu URL SVN](media/version-control-subversion1-sml.png)

2. Otwórz lub utwórz program Visual Studio for Mac Project.

3. Kliknij prawym przyciskiem myszy projekt i wybierz **formę kontroli wersji > opublikować w kontroli wersji...**:

    ![Rozpocznij publikowanie projektu](media/version-control-subversion2.png)

4. Na karcie **Połącz z repozytorium** wybierz pozycję **Subversion** z górnej listy rozwijanej.

5. Wprowadź adres URL z kroku 1. Po wprowadzeniu adresu URL pozostałe pola są wypełniane domyślnie:

    ![Okno dialogowe Wybieranie repozytorium i wprowadzanie szczegółów](media/version-control-subversion3.png)

7. Kliknij **przycisk OK,** a następnie potwierdź, naciskając przycisk **Publikuj**.

7. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia dla witryny, w której utworzysz repozytorium, jak pokazano poniżej:

    ![Wprowadzanie poświadczeń dla repozytorium wywrotowego](media/version-control-subversion5.png)

8. Wszystkie dostępne polecenia kontroli wersji powinny być teraz widoczne w menu kontroli wersji.

## <a name="see-also"></a>Zobacz też

- [Praca z podwersją](working-with-subversion.md)