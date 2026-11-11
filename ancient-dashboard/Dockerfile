# Tested focus-mode image: linux/arm64 (Pi 5) and linux/amd64.
# Source commit: f8d1756f9883a8e407f105320ec18a7c1fe8ed09
FROM docker.io/kwintend/ancienthomeassistant@sha256:c814a4247e4d3504134389b761708fc9d8c87ce29d2c8d5fa4b428441066b49e

USER root
COPY run.py /addon/run.py
# Supervisor mounts /data owned by root. Prepare a dedicated subdirectory,
# then drop privileges before starting the unchanged upstream application.
ENTRYPOINT ["python", "/addon/run.py"]
CMD []
