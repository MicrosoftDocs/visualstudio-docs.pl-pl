---
title: Zarządzanie zależnościami pakietów za pomocą requirements.txt
description: Plik requirements.txt opisuje zależności projektu. Jeśli zostanie wyświetlony projekt zawierający plik requirements.txt, można łatwo zainstalować te zależności w jednym kroku.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: f535f9d6ad4aa917cde493dfcfe089896634d706
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948117"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Zarządzaj wymaganymi pakietami za pomocą requirements.txt

Jeśli projekt jest współużytkowany z innymi osobami, należy użyć systemu kompilacji lub zaplanować skopiowanie projektu do innej lokalizacji, w której należy przywrócić środowisko, należy określić pakiety zewnętrzne wymagane przez ten projekt. Zalecanym podejściem jest użycie [ plikurequirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) zawierającego listę poleceń dla narzędzia PIP instalującego wymagane wersje pakietów zależnych. Najbardziej typowym poleceniem jest `pip freeze > requirements.txt` , które rejestruje listę bieżących pakietów środowiska w *requirements.txt*.

Technicznie wszystkie nazwy plików mogą być używane do śledzenia wymagań (przy użyciu `-r <full path to file>` podczas instalowania pakietu), ale program Visual Studio zapewnia pomoc techniczną dla *requirements.txt*:

- Jeśli załadowano projekt zawierający *requirements.txt* i chcesz zainstalować wszystkie pakiety wymienione w tym pliku, rozwiń węzeł **środowiska Python** w **Eksplorator rozwiązań**, a następnie kliknij prawym przyciskiem myszy węzeł środowisko i wybierz polecenie **Zainstaluj z requirements.txt**:

    ![Zainstaluj z requirements.txt](media/environments/environments-requirements-txt-install.png)

- Jeśli chcesz zainstalować zależności w środowisku wirtualnym, najpierw utwórz i aktywuj to środowisko, a następnie użyj polecenia **Zainstaluj z requirements.txt** . Aby uzyskać więcej informacji na temat tworzenia środowiska wirtualnego, zobacz [Korzystanie z środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Jeśli wszystkie wymagane pakiety są już zainstalowane w środowisku, można kliknąć prawym przyciskiem myszy środowisko w **Eksplorator rozwiązań** i wybrać polecenie **Generuj requirements.txt** , aby utworzyć wymagany plik. Jeśli plik już istnieje, zostanie wyświetlony monit o jego zaktualizowanie:

    ![Aktualizowanie opcji requirements.txt](media/environments/environments-requirements-txt-replace.png)

  - **Zamień cały plik** usuwa wszystkie elementy, komentarze i opcje, które istnieją.
  - **Odśwież istniejące wpisy** wykrywają wymagania pakietu i aktualizuje specyfikatory wersji, aby odpowiadały aktualnie zainstalowanej wersji.
  - **Aktualizacja i Dodawanie wpisów** odświeża wszystkie znalezione wymagania i dodaje wszystkie pozostałe pakiety na końcu pliku.

Ponieważ pliki *requirements.txt* są przeznaczone do zawieszania wymagań środowiska, wszystkie zainstalowane pakiety są zapisywane z dokładnymi wersjami. Dzięki precyzyjnej wersji można łatwo odtworzyć środowisko na innym komputerze. Pakiety są uwzględniane nawet wtedy, gdy zostały zainstalowane z zakresem wersji, jako zależność innego pakietu lub z instalatorem innym niż PIP.

Jeśli nie można zainstalować pakietu za pomocą narzędzia PIP i pojawia się on w pliku *requirements.txt* , cała instalacja nie powiedzie się. W takim przypadku ręcznie Edytuj plik, aby wykluczyć ten pakiet lub użyć [opcji PIP](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) , aby odwołać się do instalowalnej wersji pakietu. Załóżmy na przykład, że wolisz użyć [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) do skompilowania zależności i dodania `--find-links <path>` opcji do *requirements.txt*:

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
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
