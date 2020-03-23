---
title: Zarządzanie zależnościami pakietów za pomocą pliku requirements.txt
description: Plik requirements.txt opisuje zależności projektu. Jeśli otrzymasz projekt, który zawiera plik requirements.txt, można łatwo zainstalować te zależności w jednym kroku.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a1853df63354801ebf0413d3c8707135cb9bb800
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62535726"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Zarządzanie wymaganymi pakietami z plikem requirements.txt

Jeśli udostępniasz projekt innym osobom, użyj systemu kompilacji lub planujesz skopiować projekt do innej lokalizacji, w której musisz przywrócić środowisko, musisz określić pakiety zewnętrzne, których wymaga projekt. Zalecane podejście jest użycie [pliku requirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), który zawiera listę poleceń dla pip, który instaluje wymagane wersje pakietów zależnych. Najczęstszym poleceniem `pip freeze > requirements.txt`jest , który rejestruje bieżącą listę pakietów środowiska w *pliku requirements.txt*.

Technicznie każda nazwa pliku może być używana do śledzenia `-r <full path to file>` wymagań (przy użyciu podczas instalowania pakietu), ale program Visual Studio zapewnia określoną obsługę *pliku requirements.txt:*

- Jeśli załadowano projekt zawierający *plik requirements.txt* i chcesz zainstalować wszystkie pakiety wymienione w tym pliku, rozwiń węzeł **Środowiska Języka Python** w **Eksploratorze rozwiązań**, a następnie kliknij prawym przyciskiem myszy węzeł środowiska i wybierz polecenie **Zainstaluj z pliku requirements.txt:**

    ![Zainstaluj z requirements.txt](media/environments/environments-requirements-txt-install.png)

- Jeśli chcesz zainstalować zależności w środowisku wirtualnym, najpierw utwórz i aktywuj to środowisko, a następnie użyj polecenia **Zainstaluj z pliku requirements.txt.** Aby uzyskać więcej informacji na temat tworzenia środowiska wirtualnego, zobacz [Używanie środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Jeśli masz już wszystkie niezbędne pakiety zainstalowane w środowisku, możesz kliknąć prawym przyciskiem myszy to środowisko w **Eksploratorze rozwiązań** i wybrać pozycję **Generuj plik requirements.txt,** aby utworzyć niezbędny plik. Jeśli plik już istnieje, zostanie wyświetlony monit o jego zaktualizowanie:

    ![Aktualizuj opcje pliku requirements.txt](media/environments/environments-requirements-txt-replace.png)

  - **Zamień cały plik** usuwa wszystkie elementy, komentarze i opcje, które istnieją.
  - **Odśwież istniejące wpisy** wykrywa wymagania dotyczące pakietu i aktualizuje specyfikatory wersji, aby dopasować do aktualnie zainstalowanej wersji.
  - **Aktualizowanie i dodawanie wpisów** odświeża wszystkie znalezione wymagania i dodaje wszystkie inne pakiety na końcu pliku.

Ponieważ pliki *requirements.txt* mają na celu zamrożenie wymagań środowiska, wszystkie zainstalowane pakiety są zapisywane w precyzyjnych wersjach. Korzystanie z precyzyjnych wersji zapewnia łatwe odtworzenie środowiska na innym komputerze. Pakiety są dołączone, nawet jeśli zostały zainstalowane z zakresem wersji, jako zależność innego pakietu lub instalatora innego niż pip.

Jeśli pakiet nie może być zainstalowany przez pip i pojawia się w pliku *requirements.txt,* cała instalacja kończy się niepowodzeniem. W takim przypadku ręcznie edytuj plik, aby wykluczyć ten pakiet lub użyć [opcji pip w](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) celu odwoływania się do instalowalnej wersji pakietu. Na przykład może wolisz [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) użyć do skompilowania `--find-links <path>` zależności i dodać opcję do *pliku requirements.txt:*

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Zobacz też

- [Zarządzanie środowiskami języka Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybieranie interpretera dla projektu](selecting-a-python-environment-for-a-project.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna Środowiska języka Python](python-environments-window-tab-reference.md)
