---
title: Zestaw Azure SDK dla języka Python
description: Zestaw Azure SDK dla języka Python ułatwia korzystanie z usług Microsoft Azure z poziomu aplikacji Python działające na dowolnej platformie.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b9c8f5193e55d86ea4ff5e4d68fb7a66a1044d2e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062887"
---
# <a name="consume-azure-services-using-the-azure-sdk-for-python"></a>Korzystanie z usług platformy Azure przy użyciu zestawu Azure SDK dla języka Python

Zestaw Azure SDK dla języka Python ułatwia wykorzystanie i zarządzanie usługami Microsoft Azure z poziomu aplikacji w systemie Windows, MacOS i Linux.

## <a name="installation"></a>Instalacja

Zestaw Azure SDK jest instalowany z [indeksu pakietów języka Python](https://pypi.python.org/pypi/azure).

Zainstaluj **najnowsza stabilna wersja** (obsługuje język Python 2.7 i 3.x) w następujący sposób:

```command
pip install azure
```

Możesz również śledzić [zainstalowania języka Python i zestawu SDK](https://docs.microsoft.com/azure/python-how-to-install/) w dokumentacji platformy Azure.

## <a name="documentation"></a>Dokumentacja

[Zestawu Azure SDK dla Centrum deweloperów języka Python](https://docs.microsoft.com/python/azure/?view=azure-python) zawiera również liczbę przydatne zasoby, w tym liczby samouczków:

- [Tworzenie aplikacji sieci web w usłudze App Service Azuyre w systemie Linux](/azure/app-service/containers/quickstart-python).
- [Blob Storage](/azure/storage/blobs/storage-quickstart-blobs-python)
- [Table Storage](/azure/cosmos-db/table-storage-how-to-use-python)
- [Queue Storage](/azure/storage/storage-python-how-to-use-queue-storage)
- [Usługi Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Kolejki usługi Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Tematy/subskrypcje usługi Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Zarządzanie usługami](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Dla publicznych interfejsów API bez dokumentacji, testy jednostek [repozytorium SDK GitHub](https://github.com/Azure/azure-sdk-for-python) są dobrym źródłem informacji:

- [Magazyn testów jednostkowych](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Testy jednostek usługi Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Testy jednostkowe management Service](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>Obsługa

Repozytorium GitHub dla zestawu SDK znajduje się w [ https://github.com/Azure/azure-sdk-for-python ](https://github.com/Azure/azure-sdk-for-python).

[Plik problemów w repozytorium](https://github.com/Azure/azure-sdk-for-python/issues) Znajdź wszelkie problemy lub pytania dotyczące użycia zestawu SDK.
