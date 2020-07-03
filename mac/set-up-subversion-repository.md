---
title: Konfigurowanie repozytorium podwersji
description: Używanie Subversion w Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.topic: how-to
ms.openlocfilehash: 78a5dd2abbef177e2eb949d25d779a46ecc65bda
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950687"
---
# <a name="set-up-a-subversion-repository"></a>Konfigurowanie repozytorium Subversion

Subversion to scentralizowany _system kontroli wersji_, co oznacza, że istnieje jeden serwer, który zawiera wszystkie pliki i poprawki, z którego użytkownicy mogą wyewidencjonować dowolną wersję dowolnego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium podwersji, użytkownik otrzymuje migawkę repozytorium w tym momencie.

Aby można było używać Subversion dla kontroli wersji, należy ją zainstalować na maszynie. Aby sprawdzić, czy Podwersja jest zainstalowana na komputerze, użyj następującego polecenia w terminalu:

```bash
svn --version
```

To polecenie zwraca numer wersji.

Jeśli Podwersja nie jest już zainstalowana, najprostszym sposobem na jej uzyskanie jest zainstalowanie _narzędzi wiersza polecenia Xcode_. Użyj poniższego polecenia, aby zainstalować narzędzia i podwersję XCode wiersza polecenia.

```bash
xcode-select --install
```

Po zainstalowaniu podwersji na maszynie wykonaj następujące kroki, aby opublikować projekt w systemie SVN.

1. Utwórz bezpłatne repozytorium SVN w trybie online. W tym przykładzie użyto [asemblera](https://app.assembla.com/) . Po utworzeniu zostanie dostarczony adres URL, który zostanie użyty do nawiązania połączenia z repozytorium:

    ![Skopiuj adres URL SVN](media/version-control-subversion1-sml.png)

2. Otwórz lub Utwórz projekt Visual Studio dla komputerów Mac.

3. Kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Kontrola wersji > Opublikuj w kontroli wersji...**:

    ![Rozpocznij publikowanie projektu](media/version-control-subversion2.png)

4. Na karcie **Połącz z repozytorium** wybierz pozycję **podwersję** z listy rozwijanej górne.

5. Wprowadź adres URL z kroku 1. Po wprowadzeniu adresu URL inne pola są domyślnie wypełniane:

    ![Okno dialogowe Wybieranie repozytorium i wprowadzanie szczegółów](media/version-control-subversion3.png)

7. Kliknij przycisk **OK** , a następnie potwierdź, naciskając pozycję **Publikuj**.

7. Jeśli zostanie wyświetlony monit, wprowadź swoje poświadczenia dla witryny, w której tworzysz repozytorium, jak pokazano poniżej:

    ![Wprowadzanie poświadczeń dla repozytorium Subversion](media/version-control-subversion5.png)

8. Wszystkie dostępne polecenia kontroli wersji powinny teraz być widoczne w menu kontroli wersji.

## <a name="see-also"></a>Zobacz także

- [Praca z podwersją](working-with-subversion.md)