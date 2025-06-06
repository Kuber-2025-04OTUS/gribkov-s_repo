# Запуск локального окружения k8s и простейшего pod в качестве полезной нагрузки

Для выполнения использовался Kubernetes Minikube и утилита kubectl, для которой приведены использованные команды.

## Задача 
В отдельном namespace homework создать pod c контейнером, поднимающим веб-сервер, а также init-контейнером, генерирующим файл index.html, используемый веб-сервером.
При остановке контейнера с веб-сервером файл index.html должен удаляться.

## Выполнение 
### Создание namespace
*kubectl apply -f ./manifests/namespace.yaml*

#### Проверка namespace
*kubectl get ns*
![screenshot](images/namespaces.jpg)

### Создание pod
*kubectl apply -f ./manifests/configmap.yaml*

*kubectl apply -f ./manifests/pod.yaml*

#### Проверка pod
*kubectl get pods -n homework*
![screenshot](images/pods.jpg)

*kubectl get pod kubernetes-intro -n homework -o yaml*

#### Проверка веб-сервера
*kubectl port-forward pod/kubernetes-intro 8080:8000 -n homework*

Далее перейти по ссылке http://localhost:8080/
