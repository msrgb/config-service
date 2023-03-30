# Build
custom_build(
  # name of the container image
  ref = "config-service",
  # command to build the container image
  command = './gradlew bootBuildImage --imageName $EXPECTED_REF',
  # files to watch that trigger a new build
  deps = ['build.gradle', './bin/main'],
  live_update = [
    sync('./bin/main', '/workspace/BOOT-INF/classes')
  ]
)

# Deploy
k8s_yaml(['k8s/deployment.yml', 'k8s/service.yml'])

# Manage
k8s_resource('config-service', port_forwards=['8888'])