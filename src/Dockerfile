FROM invokeai/invokeai
MAINTAINER Chris Jones <cmsj@tenshu.net>

# Add the script we want
RUN apt-get install wget
RUN cd / ; wget https://raw.githubusercontent.com/invoke-ai/InvokeAI/main/scripts/invoke-new.py ; chmod +x invoke-new.py
RUN useradd --no-log-init -m -U appuser
RUN mkdir -p /data && chown -hR "appuser:appuser" /data

ENV INVOKEAI_ROOT /data
ENV TRANSFORMERS_CACHE /data/.cache
ENV INVOKE_MODEL_RECONFIGURE "--yes --default_only"

EXPOSE 9090

# Make the config and data directories volumes
VOLUME ["/data"]

ENTRYPOINT ["/invoke-new.py"]]
CMD [ "--web", "--host", "0.0.0.0", "--port", "9090" ]
