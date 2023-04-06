FROM ghcr.io/cmsj/invokeai:newer-python-and-push-cuda
MAINTAINER Chris Jones <cmsj@tenshu.net>

USER root

# Add the script we want
RUN apt-get update
RUN apt-get install wget
RUN apt-get clean
RUN rm -rf /var/cache/apt/archives
RUN cd / ; wget https://raw.githubusercontent.com/invoke-ai/InvokeAI/main/scripts/invoke-new.py ; chmod +x invoke-new.py

USER appuser

ENV INVOKEAI_ROOT /data
ENV TRANSFORMERS_CACHE /data/.cache
ENV INVOKE_MODEL_RECONFIGURE "--yes --default_only"

EXPOSE 9090

# Make the config and data directories volumes
VOLUME ["/data"]

ENTRYPOINT ["/invoke-new.py"]]
CMD [ "--web", "--host", "0.0.0.0", "--port", "9090" ]
